# pwndbg & GDB Cheatsheet for Reverse Engineers

> **Legend:**
> 
> - `[gdb]` — Native GDB command
> - `[pw]` — pwndbg only
> - `[both]` — Available in both, enhanced by pwndbg

---

## Table of Contents

1. [Execution Control](#1-execution-control)
2. [Breakpoints & Watchpoints](#2-breakpoints--watchpoints)
3. [Memory Inspection](#3-memory-inspection)
4. [Registers](#4-register-inspection--modification)
5. [Stack & Frames](#5-stack--frames)
6. [Disassembly](#6-disassembly)
7. [Heap Analysis](#7-heap-analysis)
8. [Search & Pattern](#8-search--pattern)
9. [Process & Binary Info](#9-process--binary-info)
10. [ROP & Exploit Helpers](#10-rop--exploit-helpers)

---

## 1. Execution Control

|Command|Description|Type|
|---|---|---|
|`run [args]`|Start program with optional arguments|gdb|
|`r`|Shorthand for `run`|gdb|
|`continue` / `c`|Resume execution until next breakpoint|gdb|
|`next` / `n`|Step over — execute one source line (no step into calls)|gdb|
|`step` / `s`|Step into — follow calls into functions|gdb|
|`nexti` / `ni`|Step over one machine instruction|gdb|
|`stepi` / `si`|Step into one machine instruction|gdb|
|`finish`|Run until current function returns|gdb|
|`until [line]`|Continue until given line or current line advances|gdb|
|`skip`|Skip execution of a function or file|gdb|
|`ret [value]`|Force return from current function immediately|gdb|
|`jump *addr`|Jump execution to address (no stack frame change)|gdb|
|`call func(args)`|Call a function manually from GDB|gdb|
|`kill`|Kill the running process|gdb|
|`quit` / `q`|Exit GDB|gdb|

---

## 2. Breakpoints & Watchpoints

|Command|Description|Type|
|---|---|---|
|`break *addr`|Set breakpoint at address|gdb|
|`break func`|Break at function entry|gdb|
|`break file:line`|Break at specific file and line number|gdb|
|`tbreak *addr`|Temporary breakpoint (auto-deleted after first hit)|gdb|
|`hbreak *addr`|Hardware breakpoint (useful when SW BP can't be set)|gdb|
|`info breakpoints` / `ib`|List all breakpoints|gdb|
|`delete [n]`|Delete breakpoint n (or all if omitted)|gdb|
|`disable` / `enable [n]`|Disable or re-enable breakpoint n|gdb|
|`condition n expr`|Break only when expr evaluates to true|gdb|
|`commands n`|Run GDB commands automatically when breakpoint n hits|gdb|
|`watch expr`|Watchpoint — break when expr value changes|gdb|
|`rwatch expr`|Break when expr is read|gdb|
|`awatch expr`|Break on read or write of expr|gdb|
|`catch syscall [name]`|Catch specific syscall (e.g. `open`, `execve`)|gdb|
|`catch throw`|Catch C++ exceptions being thrown|gdb|

---

## 3. Memory Inspection

|Command|Description|Type|
|---|---|---|
|`x/Nfu addr`|Examine N units of format f (`x`/`d`/`s`/`i`) at addr|gdb|
|`x/20wx $rsp`|Show 20 words as hex from the stack pointer|gdb|
|`x/10i $rip`|Disassemble 10 instructions at RIP|gdb|
|`x/s addr`|Print null-terminated string at addr|gdb|
|`x/gx addr`|Print giant (8-byte) hex at addr|gdb|
|`telescope [addr] [n]`|Follow pointer chains for n levels deep|pw|
|`tel`|Shorthand for `telescope`|pw|
|`hexdump [addr] [n]`|Hexdump n bytes starting at addr|pw|
|`memory`|Display mapped memory regions visually|pw|
|`vmmap`|Show all virtual memory mappings with permissions|pw|
|`vmmap [filter]`|Filter mappings by name (e.g. `libc`, `heap`, `stack`)|pw|
|`set {type}addr = val`|Write value to memory (e.g. `set {int}0x... = 1`)|gdb|
|`dump binary memory f a b`|Dump memory range `[a,b]` to file f|gdb|
|`restore file binary 0 a b`|Restore memory from binary file|gdb|
|`canary`|Show the stack canary value for the current binary|pw|

---

## 4. Register Inspection & Modification

|Command|Description|Type|
|---|---|---|
|`info registers` / `i r`|Show all CPU registers|gdb|
|`info registers rax`|Show value of a specific register|gdb|
|`regs`|Pretty-print all registers with context|pw|
|`print $rax`|Print register value as a GDB expression|gdb|
|`p/x $rip`|Print register as hex|gdb|
|`set $rax = 0x0`|Set a register to a value|gdb|
|`set $rip = addr`|Redirect execution to an address|gdb|
|`info float`|Show FPU/x87 registers|gdb|
|`info vector`|Show SSE/AVX vector registers|gdb|
|`context regs`|Show the register context panel only|pw|
|`context`|Show full context: regs, disasm, stack, backtrace|pw|

---

## 5. Stack & Frames

| Command             | Description                                 | Type |
| ------------------- | ------------------------------------------- | ---- |
| `backtrace` / `bt`  | Show call stack (backtrace)                 | gdb  |
| `bt full`           | Backtrace including local variables         | gdb  |
| `frame [n]`         | Select stack frame n                        | gdb  |
| `info frame`        | Show detailed info about the current frame  | gdb  |
| `info locals`       | List local variables in the current frame   | gdb  |
| `info args`         | List arguments of the current function      | gdb  |
| `up` / `down`       | Navigate one frame up / down the call stack | gdb  |
| `stack [n]`         | Print n words from the stack                | pw   |
| `telescope $rsp 20` | Follow stack pointer chain 20 levels deep   | pw   |
| `retaddr`           | Show the saved return address on the stack  | pw   |
|                     |                                             |      |

---

## 6. Disassembly

|Command|Description|Type|
|---|---|---|
|`disassemble func`|Disassemble an entire function|gdb|
|`disas /r func`|Disassemble with raw hex bytes shown|gdb|
|`disas $rip,$rip+32`|Disassemble a range starting from RIP|gdb|
|`nearpc [n]`|Show n instructions around current RIP|pw|
|`pdisass func`|Pretty-print disassembly with arrows|pw|
|`context code`|Show the code context panel only|pw|
|`set disassembly-flavor intel`|Switch to Intel syntax (recommended)|gdb|
|`set disassembly-flavor att`|Switch to AT&T syntax|gdb|
|`xinfo addr`|Print symbol + section info for an address|pw|
|`plt`|List PLT entries (libc function stub addresses)|pw|
|`got`|Show GOT entries — useful for detecting overwrites|pw|

---

## 7. Heap Analysis

|Command|Description|Type|
|---|---|---|
|`heap`|Show all heap chunks (ptmalloc / glibc)|pw|
|`heap -v`|Verbose heap walk with full metadata|pw|
|`heapinfo`|Show arena info and top chunk|pw|
|`bins`|Show all freelist bins (fast, small, large, unsorted)|pw|
|`fastbins`|Show fastbin freelist only|pw|
|`smallbins`|Show smallbin freelist only|pw|
|`largebins`|Show largebin freelist only|pw|
|`unsortedbin`|Show unsorted bin (common exploitation target)|pw|
|`tcachebins`|Show tcache freelist (glibc 2.26+)|pw|
|`malloc_chunk addr`|Parse and display malloc chunk header at addr|pw|
|`arena`|Show the main arena struct|pw|
|`top_chunk`|Show address and size of the top (wilderness) chunk|pw|
|`try_free addr`|Simulate `free(addr)` to check if it would crash|pw|

---

## 8. Search & Pattern

|Command|Description|Type|
|---|---|---|
|`search -s 'string'`|Search all mapped memory for a string|pw|
|`search -x deadbeef`|Search for a hex pattern in memory|pw|
|`search -p addr`|Search for a pointer value in memory|pw|
|`find start,end,val`|GDB native memory search|gdb|
|`cyclic [n]`|Generate a de Bruijn cyclic pattern of length n|pw|
|`cyclic -l val`|Find the offset of val in the cyclic pattern|pw|
|`pattern create [n]`|Create a pattern (alias in some pwndbg configs)|pw|
|`pattern search`|Search for pattern in registers / memory|pw|
|`xinfo addr`|Show what region/symbol an address belongs to|pw|

---

## 9. Process & Binary Info

|Command|Description|Type|
|---|---|---|
|`info proc mappings`|Show `/proc/PID/maps` — all segments|gdb|
|`info files`|List all loaded object files and their ranges|gdb|
|`info sharedlibrary`|List loaded shared libraries|gdb|
|`info functions [regex]`|List all known functions (optionally filtered)|gdb|
|`info variables [regex]`|List global variables|gdb|
|`info symbols addr`|Resolve an address to the nearest symbol|gdb|
|`checksec`|Show binary protections: NX, PIE, RELRO, canary|pw|
|`elfheader`|Print the ELF header of the loaded binary|pw|
|`elfsections`|List all ELF sections with addresses|pw|
|`libs`|List linked shared libraries|pw|
|`pid`|Show the current process PID|pw|
|`attach PID`|Attach to a running process|gdb|
|`detach`|Detach from a process without killing it|gdb|
|`set follow-fork-mode child`|Follow the child process on `fork()`|gdb|
|`show follow-fork-mode`|Show the current fork-following mode|gdb|

---

## 10. ROP & Exploit Helpers

|Command|Description|Type|
|---|---|---|
|`rop`|Search for ROP gadgets in loaded binary|pw|
|`rop --grep 'pop rdi'`|Search for a specific gadget pattern|pw|
|`ropper`|Alternative gadget finder (if ropper installed)|both|
|`got`|Print GOT — useful for ret2plt / GOT overwrite|pw|
|`plt`|Print PLT stub addresses|pw|
|`xinfo addr`|Verify gadget address and permissions|pw|
|`vmmap`|Check if an address region is executable|pw|
|`p system`|Print address of `system()` after libc loads|gdb|
|`find libc_start,+999999,"/bin/sh"`|Search for `/bin/sh` string in libc|gdb|
|`set $rip = gadget_addr`|Manually jump to a ROP gadget for testing|gdb|
|`telescope $rsp 30`|Inspect a ROP chain sitting on the stack|pw|
|`dprintf *addr,"fmt"`|Dynamic printf at address (no rebuild needed)|gdb|

---

## Quick Tips

### Essential First Steps

```
checksec          # Always run first — know your protections
vmmap             # Understand the memory layout
context           # Full situational awareness in one command
```

### Buffer Overflow Offset Finding

```
cyclic 200        # Generate pattern, paste into input
cyclic -l $rbp    # Find exact offset after crash
```

### Libc Leak → system() Address

```
p puts            # Get puts() address after it's resolved
# Calculate libc base = puts_addr - puts_offset
p system          # system() address (after libc base known)
find libc_base,+0x1000000,"/bin/sh"   # Find /bin/sh
```

### Heap Exploitation Workflow

```
heap              # Walk all chunks
bins              # Check freelists
tcachebins        # tcache state (glibc 2.26+)
malloc_chunk addr # Inspect a specific chunk header
try_free addr     # Validate a free() before it crashes
```

### GOT/PLT Overwrite

```
got               # View current GOT entries
plt               # View PLT stubs
x/gx addr        # Verify a GOT entry value
set {long}got_entry = new_addr   # Overwrite GOT entry
```

---

## Useful .gdbinit Snippet

```bash
# ~/.gdbinit
set disassembly-flavor intel
set follow-fork-mode child
set pagination off
set print pretty on

# Auto-load pwndbg
source ~/pwndbg/gdbinit.py
```

---

_Generated for Reverse Engineers — covers pwndbg + native GDB commands._