

Applications running on your operating system can contain one or more processes. Processes maintain and represent a program that’s being executed. 

Processes have a lot of other sub-components and directly interact with memory or virtual memory, making them a perfect candidate to target. The table below describes each critical component of processes and their purpose.

|                               |                                                                                                 |
| ----------------------------- | ----------------------------------------------------------------------------------------------- |
| **Process Component**         | **Purpose**                                                                                     |
| Private Virtual Address Space | Virtual memory addresses the process is allocated.                                              |
| Executable Program            | Defines code and data stored in the virtual address space                                       |
| Open Handles                  | Defines handles to system resources accessible to the process                                   |
| Security Context              | The access token defines the user, security groups, privileges, and other security information. |
| Process ID                    | Unique numerical identifier of the process                                                      |
| Threads                       | Section of a process scheduled for execution                                                    |

Handles are indeed identifiers that a process uses to access various system resources. Think of them like keys that a process holds to interact with things the operating system manages.

Let's break it down with an example:

Imagine you're writing a simple text editor. When your program wants to open a file, say "my_document.txt", the operating system does the following behind the scenes:

1. **Locates the resource:** The OS finds the "my_document.txt" file on your hard drive.
2. **Performs access checks:** The OS verifies if your program has the necessary permissions to read and/or write to this file.
3. **Creates a handle:** If the access is granted, the OS creates a unique identifier, a "handle," specifically for this open file. Let's say this handle is represented internally as the number `123`.


We will focus on four different types of process injection in this room, outlined below.

|   |   |
|---|---|
|**Injection Type**|**Function**|
|[Process Hollowing](https://attack.mitre.org/techniques/T1055/012/)|Inject code into a suspended and “hollowed” target process|
|[Thread Execution Hijacking](https://attack.mitre.org/techniques/T1055/003/)|Inject code into a suspended target thread|
|[Dynamic-link Library Injection](https://attack.mitre.org/techniques/T1055/001/)|Inject a DLL into process memory|
|[Portable Executable Injection](https://attack.mitre.org/techniques/T1055/002/)|Self-inject a PE image pointing to a malicious function into a target process|

At a high level, shellcode injection can be broken up into four steps:

1. Open a target process with all access rights.
2. Allocate target process memory for the shellcode.
3. Write shellcode to allocated memory in the target process.
4. Execute the shellcode using a remote thread.

The steps can also be broken down graphically to depict how Windows API calls interact with process memory.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e73cca6ec4fcf1309f2df86/room-content/ba04c5ef220c10b3e174bd1ca77959c6.png)



Okay, let's break down what's happening in this picture in a super simple way, like telling a short story.

Imagine you have two separate play areas:

- **The Good Play Area (Process):** This is where a normal program is running, doing its own thing. Inside this play area, it has its own building blocks like:
    
    - **DLLs (Think of them as shared toy boxes):** These contain tools and functions that many programs can use.
    - **Registers (Like the program's short-term memory):** Where it keeps track of what it's doing right now.
    - **Process Heap (Like a big container of building blocks):** Where the program can ask for more space to build things as needed.
    - **Thread Stack (Like a to-do list for different workers):** If the program has multiple helpers doing things at once.
    - **Process Memory Region (The main space where the program builds its creations):** This is the area we're most interested in.
- **The Sneaky Play Area (Malicious Process):** This is a separate program that wants to mess with the good program.
    

Here's the sneaky program's plan:

1. **Sneak Peek (OpenProcess):** The sneaky program first tries to get a special permission slip (a "handle") to the good program's play area. It's like peeking through the fence to see what's inside. The `OpenProcess` function is how it asks the "playground supervisor" (the Windows system) for this permission slip.
    
2. **Claim Some Space (VirtualAlloc):** Once the sneaky program has the permission slip, it might try to reserve a new, empty spot inside the good program's play area. The `VirtualAlloc` function is like saying, "Hey, I want to mark this empty patch of ground in your area for my own use later."
    
3. **Write a Secret Message (WriteProcessMemory):** Now, the sneaky program uses its permission slip to write something into the good program's memory. It's like sneaking in and writing a secret (and potentially harmful) message on one of the good program's building blocks using the `WriteProcessMemory` function.
    
4. **Plant a Helper (CreateRemoteThread):** The sneakiest part! The malicious program can try to plant a little helper (a "thread") inside the good program's play area. This helper will then start following the instructions written in the secret message. The `CreateRemoteThread` function is like saying, "Hey good program, can you start this new worker (that I brought) to do a task?" But this task is actually controlled by the sneaky program.
    
5. **Cause Trouble (Malicious Memory Region):** The secret message and the planted helper can then cause the good program to do things it wasn't supposed to do, potentially leading to crashes, security breaches, or other problems. This "Malicious Memory Region" is the area in the good program's memory that has been tampered with.




We will break down a basic shellcode injector to identify each of the steps and explain in more depth below.

At step one of shellcode injection, we need to open a target process using special parameters. `OpenProcess` is used to open the target process supplied via the command-line.

```cpp
processHandle = OpenProcess(
	PROCESS_ALL_ACCESS, // Defines access rights
	FALSE, // Target handle will not be inhereted
	DWORD(atoi(argv[1])) // Local process supplied by command-line arguments 
);
```

At step two, we must allocate memory to the byte size of the shellcode. Memory allocation is handled using `VirtualAllocEx`. Within the call, the `dwSize` parameter is defined using the `sizeof` function to get the bytes of shellcode to allocate.

```cpp
remoteBuffer = VirtualAllocEx(
	processHandle, // Opened target process
	NULL, 
	sizeof shellcode, // Region size of memory allocation
	(MEM_RESERVE | MEM_COMMIT), // Reserves and commits pages
	PAGE_EXECUTE_READWRITE // Enables execution and read/write access to the commited pages
);
```

At step three, we can now use the allocated memory region to write our shellcode. `WriteProcessMemory` is commonly used to write to memory regions.

```cpp
WriteProcessMemory(
	processHandle, // Opened target process
	remoteBuffer, // Allocated memory region
	shellcode, // Data to write
	sizeof shellcode, // byte size of data
	NULL
);
```

At step four, we now have control of the process, and our malicious code is now written to memory. To execute the shellcode residing in memory, we can use `CreateRemoteThread`; threads control the execution of processes.

```cpp
remoteThread = CreateRemoteThread(
	processHandle, // Opened target process
	NULL, 
	0, // Default size of the stack
	(LPTHREAD_START_ROUTINE)remoteBuffer, // Pointer to the starting address of the thread
	NULL, 
	0, // Ran immediately after creation
	NULL
);
```

We can compile these steps together to create a basic process injector. Use the C++ injector provided and experiment with process injection.

Shellcode injection is the most basic form of process injection; in the next task, we will look at how we can modify and adapt these steps for process hollowing.