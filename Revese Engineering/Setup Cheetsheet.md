
Here is your ultimate, streamlined cheat sheet for your exact setup.

### Phase 1: Debian Server Prep (`192.168.122.104`)

_Run these commands from your Windows terminal or inside your SSH session._

1. **Transfer the Target:** Move the binary from Windows to Debian.
    
    PowerShell
    
    ```
    scp C:\path\to\binary antirev@192.168.122.104:/home/antirev/
    ```
    
2. **Connect via SSH:**
    
    Bash
    
    ```
    ssh antirev@192.168.122.104 -i ~/.ssh/id_ed25519
    ```
    
3. **Prepare the Binary:** Ensure it can run and has its required libraries.
    
    Bash
    
    ```
    chmod +x binary_name
    ldd ./binary_name      # Check for "not found" errors
    ```
    
4. **Launch the Debug Server:**
    
    Bash
    
    ```
    ./linux_server         # Keep this terminal open!
    ```
    

---

### Phase 2: Windows IDA 9.0 Setup

_Do this directly inside your IDA interface._

1. **Load the File:** Drag and drop your binary into IDA and let the initial analysis finish.
    
2. **Select Debugger:** On the top toolbar, change the dropdown to **Remote Linux debugger**.
    
3. **Configure Paths:** Go to **Debugger** $\rightarrow$ **Process options...** and enter exactly this format:
    

|**Field**|**What to input**|
|---|---|
|**Application**|`/home/antirev/binary_name` _(The Linux path)_|
|**Input file**|`C:\path\to\binary_name` _(Your Windows path)_|
|**Directory**|`/home/antirev/`|
|**Hostname**|`192.168.122.104`|
|**Port / Password**|`23946` / _(Leave Password Blank)_|

---

### Phase 3: The Debugging Loop

_Your core keyboard shortcuts for reversing._

- **F2 (Breakpoint):** Click an instruction (like `main`) and press F2 to highlight it red. The program will freeze here when it runs.
    
- **F9 (Start/Run):** Launches the connection to the Debian server and runs the program until it hits your F2 breakpoint.
    
- **F8 (Step Over):** Executes the current instruction and moves to the next line. Use this to skip over boring system functions like `printf`.
    
- **F7 (Step Into):** If you are sitting on a `call` instruction, this takes you _inside_ that specific function to see its logic.
    

---

Would you like me to write up a separate, quick cheat sheet for common x86/x64 assembly instructions (like `CMP`, `TEST`, `JZ`, `JNZ`) so you know what to look for when hunting for the password checks?


