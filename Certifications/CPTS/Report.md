# Penetration Testing Report

---

|**Field**|**Details**|
|---|---|
|**Target IP**|10.174.153.115|
|**Ports Open**|22 (SSH), 80 (HTTP)|
|**Vulnerability**|Local File Inclusion (LFI)|
|**Severity**|Critical|
|**Status**|Compromised|
|**Flag**|`BHB2R{al0t_0f_w3b_vuln_cha1ned_peg4sus_c0mpr0m1s3d}`|

---

## Table of Contents

1. [Network Enumeration](#1-network-enumeration)
2. [Service Discovery](#2-service-discovery)
3. [Web Application Analysis](#3-web-application-analysis)
4. [Vulnerability Discovery — Local File Inclusion (LFI)](#4-vulnerability-discovery--local-file-inclusion-lfi)
5. [Exploitation](#5-exploitation)
6. [Proof of Compromise](#6-proof-of-compromise)
7. [Remediation Recommendations](#7-remediation-recommendations)

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

Checking the `robots.txt` file revealed disallowed paths, one of which pointed to `/internalfiles` — a sensitive directory not intended for public access.

![Robots.txt Output](../../attchments/Pasted%20image%2020260325153827.png)

### 3.3 Interesting Endpoint Discovered

Visiting the `/internalfiles` path revealed a URL with a `name` parameter used to reference files:

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

## 5. Exploitation

With the LFI vulnerability confirmed, the attack was escalated to read sensitive user files. Based on the users enumerated from `/etc/passwd`, the home directory of user **`pegasus`** was targeted.

### Payload Used

```
http://10.174.153.115/internal/files?name=../../../../home/pegasus/user.txt
```

**Result:** The `user.txt` flag file was successfully read from the filesystem.

![User Flag Retrieved](../../attchments/Pasted%20image%2020260325154133.png)

---

## 6. Proof of Compromise

| **Item**      | **Value**                                             |
| ------------- | ----------------------------------------------------- |
| **User**      | pegasus                                               |
| **File Path** | `/home/pegasus/user.txt`                              |
| **Flag**      | `BHB2R{al0t_0f_w3b_vuln_cha1ned_peg4sus_c0mpr0m1s3d}` |

The flag was retrieved without authentication, demonstrating full read access to user-owned files on the target system via chained web vulnerabilities.

---

---

# ROOT Flag

Used the command `find / -type f -perm -4000 2>/dev/null` to find the SUID binaries

![](../../attchments/Pasted%20image%2020260325161803.png)

![](../../attchments/Pasted%20image%2020260325161809.png)

SUID Permisionn on an Binnary called opscheck which is odd and intrsting i understood the binary it was used for dignostic purpose
we abused it using this paylaod 

`/usr/local/bin/opscheck "uptime && /bin/bash -p"` this gave me an root shell

![](../../attchments/Pasted%20image%2020260325161320.png)

cat the /root/root.txt to find the flag
![](../../attchments/Pasted%20image%2020260325161445.png)


**ROOT FLAG**BHB2R{new_intel:p3g4sus_pwned_r0ot_g41n3d}

| **Item**      | **Value**                                    |
| ------------- | -------------------------------------------- |
| **User**      | root                                         |
| **File Path** | `/root/root.txt`                             |
| **Flag**      | `BHB2R{new_intel:p3g4sus_pwned_r0ot_g41n3d}` |
|               |                                              |


