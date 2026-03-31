# Penetration Testing Report

---

|**Field**|**Details**|
|---|---|
|**Target IP**|10.174.153.115|
|**Ports Open**|22 (SSH), 80 (HTTP)|
|**Vulnerabilities**|Local File Inclusion (LFI), SUID Binary Abuse|
|**Severity**|Critical|
|**Status**|Fully Compromised (Root)|
|**User Flag**|`BHB2R{al0t_0f_w3b_vuln_cha1ned_peg4sus_c0mpr0m1s3d}`|
|**Root Flag**|`BHB2R{new_intel:p3g4sus_pwned_r0ot_g41n3d}`|

---

## Table of Contents

1. [Network Enumeration](#1-network-enumeration)
2. [Service Discovery](#2-service-discovery)
3. [Web Application Analysis](#3-web-application-analysis)
4. [Vulnerability Discovery — Local File Inclusion (LFI)](#4-vulnerability-discovery--local-file-inclusion-lfi)
5. [Exploitation — User Flag](#5-exploitation--user-flag)
6. [Privilege Escalation — Root Flag](#6-privilege-escalation--root-flag)
7. [Proof of Compromise](#7-proof-of-compromise)
8. [Remediation Recommendations](#8-remediation-recommendations)

---

## 1. Network Enumeration

The first step was to identify the IP address of the target machine within the network.

**Target IP Identified: `10.174.153.115`**

![Target IP Discovery](../../attchments/Pasted%20image%2020260325153442.png)

---

## 2. Service Discovery

A basic Nmap scan was performed against the target to enumerate open ports and running services.

**Result:** Two ports were found open:

- **Port 22** — SSH
- **Port 80** — HTTP

![Nmap Scan Results](../../attchments/Pasted%20image%2020260325153646.png)

---

## 3. Web Application Analysis

### 3.1 Landing Page

Navigating to `http://10.174.153.115` revealed a web application hosting a login page.

![Web Login Page](../../attchments/Pasted%20image%2020260325153739.png)

### 3.2 Robots.txt Disclosure

Checking the `robots.txt` file revealed disallowed paths, one of which pointed to `/internal/files` — a sensitive directory not intended for public access.

![Robots.txt Output](../../attchments/Pasted%20image%2020260325153827.png)

### 3.3 Interesting Endpoint Discovered

Visiting the `/internal/files` path revealed a URL with a `name` parameter used to reference files:

```
http://10.174.153.115/internal/files?name=report.txt
```

The use of a `name` parameter to fetch files on the server is a strong indicator of a **Local File Inclusion (LFI)** vulnerability.

![Internal Files Endpoint](../../attchments/Pasted%20image%2020260325153927.png)

---

## 4. Vulnerability Discovery — Local File Inclusion (LFI)

### Description

The `name` parameter in the `/internal/files` endpoint was not properly sanitized, allowing an attacker to traverse the directory structure using `../` sequences and read arbitrary files from the server's filesystem.

### Proof of Concept — `/etc/passwd` Read

The following payload was used to traverse out of the web root and read the system's `/etc/passwd` file:

```
http://10.174.153.115/internal/files?name=../../../../etc/passwd
```

**Result:** The server returned the full contents of `/etc/passwd`, confirming the LFI vulnerability.

![/etc/passwd via LFI](../../attchments/Pasted%20image%2020260325154033.png)

---

## 5. Exploitation — User Flag

With the LFI vulnerability confirmed, the attack was escalated to read sensitive user files. Based on the users enumerated from `/etc/passwd`, the home directory of user **`pegasus`** was targeted.

### Payload Used

```
http://10.174.153.115/internal/files?name=../../../../home/pegasus/user.txt
```

**Result:** The `user.txt` flag file was successfully read from the filesystem.

![User Flag Retrieved](../../attchments/Pasted%20image%2020260325154133.png)

---

## 6. Privilege Escalation — Root Flag

### 6.1 SUID Binary Enumeration

After obtaining a foothold on the system via the LFI vulnerability, the next objective was to escalate privileges to `root`. The following command was run to locate all binaries with the SUID bit set:

```bash
find / -type f -perm -4000 2>/dev/null
```

![SUID Binary Enumeration](../../attchments/Pasted%20image%2020260325161803.png)

![SUID Binary List](../../attchments/Pasted%20image%2020260325161809.png)

### 6.2 Suspicious Binary — `opscheck`

Among the standard SUID binaries, an unusual binary was identified:

```
/usr/local/bin/opscheck
```

This binary is non-standard and not part of any default Linux installation. Analysis of the binary revealed it was designed for **diagnostic/system health checking purposes** — it accepted a command string and executed it as part of its operation. Because it runs with SUID permissions (as root), any command passed to it inherits root privileges.

### 6.3 Exploitation — Root Shell via `opscheck`

The following payload was used to abuse the SUID binary and spawn a privileged Bash shell:

```bash
/usr/local/bin/opscheck "uptime && /bin/bash -p"
```

**Breakdown:**

- `uptime` — satisfies any argument validation the binary may perform
- `&&` — chains a second command upon success
- `/bin/bash -p` — launches Bash in privileged mode, preserving the effective UID of `root`

**Result:** A root shell was obtained.

![Root Shell Obtained](../../attchments/Pasted%20image%2020260325161320.png)

### 6.4 Root Flag Retrieved

With root access confirmed, the final flag was read from `/root/root.txt`:

```bash
cat /root/root.txt
```

![Root Flag](../../attchments/Pasted%20image%2020260325161445.png)

---

## 7. Proof of Compromise

|**Item**|**Value**|
|---|---|
|**User**|pegasus|
|**User Flag**|`BHB2R{al0t_0f_w3b_vuln_cha1ned_peg4sus_c0mpr0m1s3d}`|
|**Root Method**|SUID Binary Abuse (`/usr/local/bin/opscheck`)|
|**Root Flag**|`BHB2R{new_intel:p3g4sus_pwned_r0ot_g41n3d}`|

Full system compromise was achieved — from unauthenticated web access to a root shell — by chaining an LFI vulnerability with a misconfigured SUID binary.

---

## 8. Remediation Recommendations

|**Priority**|**Finding**|**Recommendation**|
|---|---|---|
|Critical|Local File Inclusion (LFI)|Validate and whitelist all file paths server-side. Never pass user-supplied input directly to filesystem functions.|
|Critical|SUID Binary — `opscheck`|Remove the SUID bit from `opscheck` immediately (`chmod u-s /usr/local/bin/opscheck`). If shell execution is required, redesign with privilege separation and strict input validation.|
|High|`robots.txt` Path Disclosure|Remove sensitive internal paths from `robots.txt`. Public disclosure of internal routes directly assists attackers.|
|High|Sensitive Files Accessible via Web|Ensure user home directories and sensitive files are never within scope of the web application's file access.|
|Medium|No Authentication on `/internalfiles`|Restrict internal file endpoints with proper authentication and authorisation controls.|

---

_Report generated based on assessment of target `10.174.153.115`. All testing was performed in an authorised environment._