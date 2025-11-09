
Windows distinguishes hardware access by two distinct modes: **user** and **kernel mode**. These modes determine the hardware, kernel, and memory access an application or driver is permitted. API or system calls interface between each mode, sending information to the system to be processed in kernel mode.



|                                    |                                  |
| ---------------------------------- | -------------------------------- |
| **User mode**                      | **Kernel mode**                  |
| No direct hardware access          | Direct hardware access           |
| Access to "owned" memory locations | Access to entire physical memory |


![Diagram showing the user mode at the top and kernel mode at the bottom, divided by the switching point](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e73cca6ec4fcf1309f2df86/room-content/3099761e193a0fa0eab05432b07e0537.png)


