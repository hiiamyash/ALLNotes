
## **Learning Objectives

- Understand and interact with Windows processes and their underlying technologies.
- Learn about core file formats and how they are used.
- Interact with Windows internals and understand how the Windows kernel operates.


## **Process


A **process** is just a running program on your computer. Every app you open creates at least one process. Some apps might have multiple processes running at the same time.

### What Makes Up a Process?

Think of a process like a box that holds everything a program needs to run. According to Microsoft, a process includes:

- **Memory space** (where it stores information)
    
- **The actual code** (instructions the program follows)
    
- **Open files and connections** (like a document it’s editing or an internet connection)
    
- **A security level** (to control what it can do)
    
- **A unique ID** (to track the process)
    
- **Settings** (like environment variables)
    
- **A priority level** (how important it is for the computer)
    
- **At least one thread** (the actual work being done)
    


### How Attackers Can Abuse Processes

Hackers try to hide harmful programs inside real processes so they don’t get detected. Here are some tricks they use:

- **Process Injection** → Hiding malicious code inside a real process
    
- **Process Hollowing** → Replacing a real process with a fake one
    
- **Process Masquerading** → Renaming a harmful process to look like a safe one



**We can also explain a process at a lower level as it resides in the virtual address space. The table and diagram below depict what a process looks like in memory.

|                     |                                               |
| ------------------- | --------------------------------------------- |
| **Component  <br>** | **Purpose**                                   |
| Code                | Code to be executed by the process.           |
| Global Variables    | Stored variables.                             |
| Process Heap        | Defines the heap where data is stored.        |
| Process Resources   | Defines further resources of the process.     |
| Environment Block   | Data structure to define process information. |

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e73cca6ec4fcf1309f2df86/room-content/66320022b6b57f3c40e135d66de3c1d9.png)


|   |   |   |
|---|---|---|
|**Value/Component  <br>**|**Purpose  <br>**|**Example**|
|Name|Define the name of the process, typically inherited from the application|conhost.exe|
|PID|Unique numerical value to identify the process|7408|
|Status|Determines how the process is running (running, suspended, etc.)|Running|
|User name|User that initiated the process. Can denote privilege of the process|SYSTEM|

