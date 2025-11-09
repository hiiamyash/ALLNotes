#linux #basics 
### **1.`/bin` (Binary Executables)**

- Contains essential user command binaries.
- Used for system boot and single-user mode.
- Examples:
    - `/bin/ls` → Lists directory contents.
    - `/bin/cp` → Copies files and directories.

---

### **2. `/boot` (Boot Files)**

- Stores boot-related files like the Linux kernel and bootloader (GRUB).
- Examples:
    - `/boot/vmlinuz` → Compressed Linux kernel image.
    - `/boot/grub/grub.cfg` → GRUB bootloader configuration.

---

### **3. `/dev` (Device Files)**

- Contains device files that interact with hardware.
- Examples:
    - `/dev/sda` → Represents a hard disk.
    - `/dev/null` → Discards all data written to it.
    - `/dev/tty` → Terminal device file.

---

### **4. `/etc` (Configuration Files)**

- Contains system-wide configuration files.
- Examples:
    - `/etc/passwd` → Stores user account details.
    - `/etc/hosts` → Maps hostnames to IP addresses.
    - `/etc/ssh/sshd_config` → Configuration file for SSH.

---

### **5. `/home` (User Home Directories)**

- Contains personal files and configurations for users.
- Example:
    - `/home/user/.bashrc` → User’s Bash configuration.

---

### **6. `/lib` (Shared Libraries)**

- Stores essential shared libraries for binaries in `/bin` and `/sbin`.
- Examples:
    - `/lib/x86_64-linux-gnu/libc.so.6` → Standard C library.

---

### **7. `/lib32`, `/lib64` (32-bit and 64-bit Libraries)**

- Contains 32-bit (`/lib32`) and 64-bit (`/lib64`) shared libraries.

---

### **8. `/lost+found` (Recovery Directory)**

- Stores orphaned files recovered after an unexpected shutdown or file system check.
- Example: If the system crashes, you may find lost files in `/lost+found`.

---

### **9. `/media` (Mount Points for Removable Media)**

- Mount point for external devices like USB drives and DVDs.
- Example:
    - `/media/usb-drive` → Mounted USB storage.

---

### **10. `/mnt` (Temporary Mount Directory)**

- Used to manually mount filesystems.
- Example:

```
sudo mount /dev/sdb1 /mnt

```

 <h3>11. /opt</h3>

- Used for manually installed software (not managed by package manager).
- Example:
    - `/opt/google/chrome/` → Google Chrome installed manually.

---

### **12. `/proc` (Process Information)**

- Virtual filesystem providing process and system information.
- Examples:
    - `/proc/cpuinfo` → CPU details.
    - `/proc/meminfo` → Memory usage details.
    - `/proc/1234/` → Information about process with PID 1234.

---

### **13. `/root` (Root User Home Directory)**

- Home directory for the root user (superuser).
- Example:
    - `/root/.bashrc` → Root user’s Bash configuration.

---

### **14. `/run` (Runtime Data)**

- Stores volatile runtime data like process IDs and sockets.
- Example:
    - `/run/sshd.pid` → PID file for SSH service.

---

### **15. `/sbin` (System Binaries)**

- Contains essential binaries for system administration.
- Examples:
    - `/sbin/reboot` → Reboots the system.
    - `/sbin/fsck` → Filesystem check and repair.

---

### **16. `/snap` (Snap Packages)**

- Used by Ubuntu’s Snap package manager for containerized applications.
- Example:
    - `/snap/bin/firefox` → Firefox installed as a Snap package.

---

### **17. `/srv` (Service Data)**

- Stores data for system services like web or FTP servers.
- Example:
    - `/srv/http/` → Root directory for a web server.

---

### **18. `/sys` (Kernel and Hardware Information)**

- Virtual filesystem providing real-time hardware and system information.
- Examples:
    - `/sys/class/net/eth0/` → Information about network interface `eth0`.

---

### **19. `/tmp` (Temporary Files)**

- Stores temporary files that get deleted on reboot.
- Example:
