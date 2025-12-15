



This document outlines the technical architecture and implementation roadmap for **Ghost-Rig**, an Ephemeral Infrastructure Management (EIM) system.

The objective is to engineer a highly portable, single-binary CLI that orchestrates the lifecycle of Red Team infrastructure (redirectors, C2 relays, phishing gateways) by wrapping Terraform core logic within a high-performance Go runtime.

### 1. System Architecture

The system utilizes a **Controller-Agentless** architecture. The Go binary acts as the controller, managing a local state database and spawning isolated subprocesses for Infrastructure-as-Code (IaC) execution.

#### High-Level Data Flow

1. **Input:** Operator selects an Infrastructure Template via TUI.
    
2. **Orchestration:** The Core Controller instantiates a new workspace and generates a unique Run ID.
    
3. **Execution:** The Terraform Wrapper injects ephemeral SSH keys and provider credentials, then executes `terraform apply`.
    
4. **Persistence:** State metadata (IPs, IDs, Timestamps) is synchronized to a local SQLite database.
    
5. **Presentation:** The TUI polls the database to render real-time status updates.
    

---

### 2. Technology Stack & Dependencies

- **Runtime:** Go (Golang) 1.22+
    
- **IaC Engine:** Terraform (embedded binary or path-resolved).
    
- **TUI Framework:** `charmbracelet/bubbletea` (Elm Architecture: Model-View-Update).
    
- **Database:** SQLite3 (via `mattn/go-sqlite3`).
    
- **Terraform Wrapper:** `hashicorp/terraform-exec` (Official Go wrapper for the TF CLI).
    
- **Configuration:** `spf13/viper` (Environment variable and config file parsing).
    

---

### 3. Core Component Design

#### A. The Template Engine (Infrastructure Modules)

Instead of dynamic generation, we use `go:embed` to compile verified Terraform modules directly into the binary. This ensures portability and eliminates external dependencies.

**Directory Structure within Binary:**

Plaintext

```
/internal/templates/
    /digitalocean-redirector/
        main.tf
        variables.tf
        cloud-init.yaml (Hardening configs: UFW, Fail2Ban)
    /aws-smtp-relay/
        ...
```

**Interface Definition:**

Go

```
type Template struct {
    ID          string
    Name        string
    Provider    string // AWS, DO, Azure
    Variables   []VariableDefinition // e.g., "Target_IP", "Domain"
    CostPerHour float64
}
```

#### B. The State Store (Database Schema)

We maintain a relational state independent of `terraform.tfstate` to track operational logic (Project IDs, Operator ownership, billing).

**Schema (`schema.sql`):**

SQL

```
CREATE TABLE deployments (
    id TEXT PRIMARY KEY,             -- UUID
    template_id TEXT,                -- e.g., "do-redirector"
    workspace_path TEXT,             -- Local path to TF execution dir
    status TEXT,                     -- PROVISIONING, RUNNING, ERROR, DESTROYED
    public_ip TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    ssh_private_key_path TEXT        -- Path to ephemeral key
);

CREATE TABLE logs (
    deployment_id TEXT,
    log_entry TEXT,
    timestamp DATETIME,
    FOREIGN KEY(deployment_id) REFERENCES deployments(id)
);
```

#### C. The Workspace Manager

To prevent state collisions, every deployment must run in an isolated directory.

**Logic:**

1. Generate UUID `550e8400-e29b...`.
    
2. Create directory `~/.ghost-rig/workspaces/<UUID>/`.
    
3. Copy the embedded template files (main.tf) into this directory.
    
4. Generate an ephemeral SSH keypair (`id_rsa`, `id_rsa.pub`) specifically for this instance.
    
5. Initialize `terraform-exec` pointing to this directory.
    

---

### 4. Implementation Logic: The Provisioning Workflow

This process must be handled asynchronously (via Goroutines) to prevent blocking the TUI.

**Step 1: Initialization**

- User selects "DigitalOcean Redirector".
    
- Input prompt: `Target_IP`, `API_Token`.
    
- System creates the workspace directory and populates `main.tf`.
    

**Step 2: Execution (The `tfexec` Wrapper)**

Go

```
import "github.com/hashicorp/terraform-exec/tfexec"

func Provision(ctx context.Context, dir string, vars map[string]string) error {
    tf, err := tfexec.NewTerraform(dir, execPath)
    
    // 1. Init
    err = tf.Init(ctx, tfexec.Upgrade(true))
    
    // 2. Plan (Safety check)
    _, err = tf.Plan(ctx)
    
    // 3. Apply
    // We pass variables via -var flags programmatically
    varOptions := []tfexec.ApplyOption{}
    for k, v := range vars {
        varOptions = append(varOptions, tfexec.Var(k+"="+v))
    }
    
    return tf.Apply(ctx, varOptions...)
}
```

**Step 3: Output Parsing**

- Terraform outputs (defined in `outputs.tf`) must be captured.
    
- The Go controller extracts `public_ip` using `tf.Output(ctx)` and updates the SQLite database record from `PROVISIONING` to `RUNNING`.
    

---

### 5. Implementation Logic: The Teardown Workflow

Security is paramount during deprovisioning. We must ensure no artifacts remain.

**Step 1: Destruction**

- Execute `tf.Destroy(ctx)`.
    

**Step 2: Artifact Sanitization**

- **Secure Wipe:** Use file overwriting (seeking to 0 and writing random bytes) on the `terraform.tfstate` and the generated SSH private keys before file deletion.
    
- **Workspace Cleanup:** `os.RemoveAll(workspaceDir)`.
    
- **DB Update:** Mark status as `DESTROYED` (retain record for audit logs).
    

---

### 6. User Interface (Bubbletea TUI)

The UI follows the Model-Update-View (MUV) pattern.

**The Model:**

Go

```
type Model struct {
    deployments []Deployment // Slice of active infra
    spinner     spinner.Model // For async operations
    table       table.Model   // Main dashboard view
    activeTab   int           // 0: Dashboard, 1: Wizard, 2: Logs
}
```

**The Update Loop (Concurrency Handling):**

- Since `terraform apply` takes time, it runs in a `tea.Cmd`.
    
- The TUI sends a `MsgProvisionStart`.
    
- A Goroutine spawns, runs Terraform, and sends `MsgProvisionSuccess` or `MsgProvisionError` back to the UI loop.
    
- The UI updates the list without freezing.
    

---

### 7. Security & OpSec Considerations

1. **State Isolation:**
    
    - Do not use remote state buckets (S3) by default to avoid creating attribution trails. Keep state local, encrypted if possible, and ephemeral.
        
2. **Key Management:**
    
    - Never reuse SSH keys between deployments. The tool generates a new keypair for every single droplet/EC2 instance.
        
3. **Traceability:**
    
    - The `User-Agent` string of the Terraform provider should be overridden if possible to avoid flagging generic Terraform traffic patterns, though this is often controlled by the provider plugin.
        

---

### 8. Development Roadmap

**Phase 1: Core Mechanics (Non-Interactive)**

- Build the `InfrastructureManager` struct that handles copying embedded files to temp dirs.
    
- Implement `tfexec` to successfully run `apply` and `destroy` on a dummy local file provider.
    
- Implement SQLite logging.
    

**Phase 2: The TUI Layer**

- Build the Dashboard Table view using `charmbracelet/bubbles/table`.
    
- Implement the asynchronous command pattern to run the Phase 1 logic without blocking the UI rendering.
    

**Phase 3: Production Hardening**

- Add Cloudflare DNS integration (via Terraform provider) for automated domain fronting.
    
- Implement the "Secure Wipe" logic for state files.
    

### 9. Immediate Action Items

1. **Define the Interface:** Create `internal/core/engine.go` defining the methods `CreateDeployment`, `GetStatus`, and `DestroyDeployment`.
    
2. **Scaffold the Database:** Create the `schema.sql` and the Go code to initialize it on startup.
    
3. **Prototype `tfexec`:** Write a small script that hardcodes a path to a `.tf` file and successfully runs `terraform apply` using the Go wrapper. This proves the core technical hypothesis.