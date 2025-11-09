
# GhostRunner

GhostRunner is a post-exploitation tool designed to demonstrate advanced process injection techniques. It allows security researchers and red teamers to experiment with different methods of code injection against live processes in controlled environments.

⚠️ **Disclaimer:** GhostRunner is for **educational and research purposes only**. Use it only in lab environments or systems you are explicitly authorized to test. Misuse may violate laws and result in severe consequences.

---

## ✨ Features

- **DLL Injection** – Load custom DLLs into a remote process.
- **Shellcode Injection** – Inject and execute raw shellcode.
- **APC Injection** – Queue shellcode execution in target process threads.
- **Process Hollowing** – Replace the code of a legitimate process with a malicious payload.

---

## 🚀 Techniques & Usage

### 🔹 DLL Injection
Injects a DLL into the specified process using the `LoadLibrary` technique.
```bash
ghostrunner dll <PID> <DLL_PATH>
