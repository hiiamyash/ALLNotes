
# crackmes.one — Reverse Engineering Challenge Guide

> **Platform:** [crackmes.one](https://crackmes.one) **Zip password (all downloads):** `crackmes.one` **Last updated:** April 2026

A curated list of reverse engineering challenges from crackmes.one for both Linux and Windows, sorted by difficulty. Each entry includes a direct challenge link, a writeup link, the binary type, and the key techniques you need to solve it.

---

## Recommended Tools

|Purpose|Linux|Windows|
|---|---|---|
|Disassembler / Decompiler|Ghidra, radare2, Cutter|Ghidra, IDA Free, Binary Ninja|
|Debugger|GDB, ltrace, strace|x64dbg, x32dbg, WinDbg|
|Static analysis|`strings`, `file`, `readelf`|CFF Explorer, PEiD, PE-bear|
|Scripting|Python, angr|Frida, Python|
|Packer detection|`upx -d`, `file`|PEiD, Detect-It-Easy (DIE)|

---

---

# 🐧 LINUX Challenges

---

## ✅ EASY

---

### 1. keyg3nme — by ezman

|Field|Info|
|---|---|
|**Binary**|64-bit ELF|
|**Goal**|Find a valid key|
|**Techniques**|Ghidra decompiler, modulo check|
|**Challenge**|https://crackmes.one/crackme/5da31ebc33c5d46f00e2c661|
|**Writeup**|https://medium.com/@Asm0d3us/1-crackmes-one-beginner-friendly-reversing-challenges-6df94ea6b29d|

**Description:** The binary asks you to enter a key. The validation function checks whether your input is divisible by `1223` (0x4C7). Use `strings` or Ghidra's decompiler to locate the modulo comparison, then supply any multiple of 1223 as your key.

**Key technique:** Spotting a `mod` / remainder check in decompiled C. Perfect first challenge.

---

### 2. easy_reverse — by cbm-hackers

|Field|Info|
|---|---|
|**Binary**|64-bit ELF|
|**Goal**|Find the correct password|
|**Techniques**|Ghidra, `strings`, assembly reading|
|**Challenge**|https://crackmes.one/crackme/5b8a37a433c5d45fc286ad83|
|**Writeup**|https://thecatism.github.io/Reverse-Engineering-Crackme-Files-Easy_Reverse/|

**Description:** A 64-bit ELF that takes a password as a command-line argument. Running `strings` gives you candidate strings. Ghidra decompilation shows the comparison logic clearly. Good for getting comfortable with the ELF analysis workflow.

**Key technique:** `file` → `strings` → Ghidra decompile → read `strcmp` or equivalent.

---

### 3. PrettyDamnEasy — by nutcake

|Field|Info|
|---|---|
|**Binary**|64-bit ELF|
|**Goal**|Find the password|
|**Techniques**|radare2, `s main`, disassembly reading|
|**Challenge**|https://crackmes.one/crackme/5b8a37a433c5d45fc286ad83|
|**Writeup**|https://medium.com/@0xINT3/crackmes-one-challenges-eb74991b43c7|

**Description:** Prompts for a password at runtime. Use radare2 (`aaa` → `s main` → `pdf`) to jump straight to `main` and read the comparison from the disassembly without needing a decompiler.

**Key technique:** First use of radare2 for navigation and basic disassembly reading.

---

### 4. Kawaii Flesh — simple crackme

|Field|Info|
|---|---|
|**Binary**|32-bit ELF|
|**Goal**|Find the key and the easter egg|
|**Techniques**|`ltrace`, MD5 hash cracking|
|**Challenge**|https://crackmes.one/ (search "Kawaii Flesh")|
|**Writeup**|https://kamransaifullah.medium.com/simple-crackme-kawaii-flesh-writeup-f01ef30031a6|

**Description:** Running the binary under `ltrace` reveals an MD5 hash being compared against the user's input. Paste the hash into an online MD5 cracker to recover the password. Introduces hash-based validation as a concept.

**Key technique:** `ltrace` interception of library calls to reveal the comparison value.

---

### 5. crackme0x00a — ioli series (entry)

|Field|Info|
|---|---|
|**Binary**|32-bit ELF|
|**Goal**|Find the password|
|**Techniques**|`strings`, basic static analysis|
|**Challenge**|https://crackmes.one/ (search "ioli crackme")|
|**Writeup**|https://irkenkitties.com/blog/2016/04/12/reversing-crackme-challenges/|

**Description:** The very first challenge in the classic IOLI crackme series. The password is stored in plaintext and `strings` finds it immediately. Good warm-up before the series escalates.

**Key technique:** `strings` as the first tool; understanding why it works here and why it won't later.

---

## ⚠️ INTERMEDIATE

---

### 6. Crackme-one (rev) — Asm0d3us series Part 2

|Field|Info|
|---|---|
|**Binary**|64-bit ELF shared object|
|**Goal**|Dynamically generated flag|
|**Techniques**|`ltrace`, Ghidra, `strncmp` interception|
|**Challenge**|https://crackmes.one/|
|**Writeup**|https://medium.com/@Asm0d3us/part-2-crackmes-one-beginner-friendly-reversing-challenges-5e58a8a42e26|

**Description:** The flag is not hardcoded — it is generated from your input. `ltrace` intercepts the `strncmp` call and reveals what the binary is comparing your input against at runtime. The twist: only the first 8 characters matter, so any input starting with the right prefix passes.

**Key technique:** `ltrace` for dynamic library call tracing; understanding partial string comparison.

---

### 7. simple_ctf — hash comparison challenge

|Field|Info|
|---|---|
|**Binary**|ELF binary|
|**Goal**|Find an input that passes the hash check|
|**Techniques**|Ghidra, custom hash reversal|
|**Challenge**|https://crackmes.one/|
|**Writeup**|https://medium.com/@nomanprodhan/cracking-the-simple-ctf-from-crackmes-one-afc12706e7ad|

**Description:** Contains custom functions `ctfhash` and `compare_hashes`. You must decompile both in Ghidra, understand the transformation applied to your input, and work backwards to find an input that produces the expected digest.

**Key technique:** Reading and reversing a custom hash function in Ghidra's decompiler.

---

### 8. crackme by raxer

|Field|Info|
|---|---|
|**Binary**|x64 ELF|
|**Goal**|Find the password (no bytepatching)|
|**Techniques**|x64dbg, control flow tracing, XOR/AND analysis|
|**Challenge**|https://crackmes.one/crackme/5ed5b3c833c5d449d91ae6d0|
|**Writeup**|https://github.com/v0idMrK/CrackMe-challenge-writeup-1|

**Description:** Patching is not allowed — you must fully reverse the password algorithm. A character-by-character loop applies XOR and AND operations against a reference string. Requires stepping through each iteration and reconstructing the expected key.

**Key technique:** Manual control-flow tracing, understanding bit-level character comparison loops.

---

### 9. noprelo — by kellek

|Field|Info|
|---|---|
|**Binary**|64-bit ELF (stripped, PIE)|
|**Goal**|Show the "Good boy" message|
|**Techniques**|IDA / Ghidra, anti-ptrace bypass|
|**Challenge**|https://crackmes.one/ (search "noprelo")|
|**Writeup**|https://medium.com/@clem.boin/noprelo-crackme-writeup-fc9f1043d165|

**Description:** The binary uses `ptrace(0,0,1,0)` in `main` to detect debuggers — `ltrace` immediately exits. You must load the binary in IDA/Ghidra statically, patch or bypass the ptrace check, then follow the actual validation logic to find the correct input.

**Key technique:** Recognizing and defeating `ptrace`-based anti-debug in a Linux binary.

---

### 10. Simple obfuscation — by BinaryNewbie

|Field|Info|
|---|---|
|**Binary**|ELF|
|**Goal**|Find the flag (no patching)|
|**Techniques**|Ghidra, ptrace bypass, key derivation|
|**Challenge**|https://crackmes.one/crackme/5d6da7bc33c5d46f00e2c3a3|
|**Writeup**|https://crackmes.one/crackme/5d6da7bc33c5d46f00e2c3a3 (solutions tab)|

**Description:** Light obfuscation layered on top of a ptrace anti-debug check. Patching is not allowed, so you must bypass ptrace by manipulating register values at the right breakpoint, then reverse the key derivation to produce the correct flag.

**Key technique:** Register manipulation to bypass anti-debug without modifying the binary on disk.

---

### 11. crackme05 — keygen challenge

|Field|Info|
|---|---|
|**Binary**|64-bit ELF|
|**Goal**|Write a keygen (no patching)|
|**Techniques**|Ghidra, serial validation algorithm, Python keygen|
|**Challenge**|https://crackmes.one/ (search "crackme05")|
|**Writeup**|https://medium.com/@satadrumemini/ever-since-i-got-into-cybersecurity-ive-been-drawn-to-the-low-level-workings-of-computers-499c609e65f3|

**Description:** The binary validates a serial passed as a command-line argument. You must run it with `-h` first to understand the expected format, then decompile the serial validation in Ghidra and write a Python keygen that produces valid serials on demand.

**Key technique:** Full algorithm reversal and keygen authoring — the true goal of crackmes.

---

## 🔴 HARD

---

### 12. crackme0x03–0x05 — ioli series (advanced)

|Field|Info|
|---|---|
|**Binary**|32-bit ELF series|
|**Goal**|Find the password through multi-function arithmetic|
|**Techniques**|radare2, GDB, register math tracing|
|**Challenge**|https://crackmes.one/ (search "ioli")|
|**Writeup**|https://irkenkitties.com/blog/2016/04/12/reversing-crackme-challenges/|

**Description:** The later stages of the IOLI series call nested validation functions that apply arithmetic transformations to derive the password (e.g. password = 338724 derived from register arithmetic). Requires careful tracing of the stack frame and register state across multiple function calls.

**Key technique:** Multi-function call graph analysis, manual register/stack tracking, `cdecl` calling convention understanding.

---

### 13. crackmes.one CTF 2026 — Linux challenges (official)

|Field|Info|
|---|---|
|**Binary**|Multiple (ELF, multi-platform)|
|**Goal**|Various — CTF-grade|
|**Techniques**|Full reversing suite|
|**Challenge + Writeups**|https://github.com/crackmesone/ctf-2026-challenges-public|

**Description:** Official competition challenges from the 2026 crackmes.one CTF event. The public GitHub repository includes handout binaries, source code, and official writeups for select challenges. These are the hardest reversing tasks on the platform and serve as excellent benchmarks for advanced practitioners.

**Key technique:** Everything — custom packers, anti-debug, obfuscation, algorithm reversal.

---

---

# 🪟 WINDOWS Challenges

---

## ✅ EASY

---

### 1. find_the_pass — jaybailey series

|Field|Info|
|---|---|
|**Binary**|C/C++ PE32|
|**Goal**|Find the password (supplied as argument)|
|**Techniques**|`strings`, static analysis, Wine on Linux|
|**Challenge**|https://crackmes.one/|
|**Writeup**|https://jaybailey216.com/find-the-pass/|

**Description:** A Windows PE binary solvable without a debugger — `strings` reveals a candidate password almost immediately. Also demonstrates the full Windows PE static analysis workflow, including running it on Kali via Wine when a Windows VM is unavailable.

**Key technique:** `strings` on a PE binary; understanding why Wine lets you do dynamic analysis of Windows binaries on Linux.

---

### 2. Windows crackme — deepak series (Part 2)

|Field|Info|
|---|---|
|**Binary**|PE32 (.exe)|
|**Goal**|Find the correct password|
|**Techniques**|x32dbg, breakpoints, string reference search|
|**Challenge**|https://crackmes.one/crackme/641d518233c5d447bc761c0f|
|**Writeup**|https://medium.com/@deepakkeshav98/reverse-engineering-crackmes-one-cracking-easy-crackmes-part-2-3533979f9f8f|

**Description:** The binary first validates password length (must be 18 chars) before comparing against a hardcoded string. Set a breakpoint at "Enter the password:" in x32dbg, then trace the two-stage check using the string reference search feature.

**Key technique:** x32dbg string reference search to locate validation code; multi-stage validation logic.

---

### 3. Baby Keygen series — by 2ourc3

|Field|Info|
|---|---|
|**Binary**|PE64|
|**Goal**|Find valid serial format|
|**Techniques**|x64dbg, control flow obfuscation analysis|
|**Challenge**|https://crackmes.one/crackme/63a38ce833c5d43ab4ecf076|
|**Writeup**|https://crackmes.one/crackme/63a38ce833c5d43ab4ecf076 (solutions tab)|

**Description:** A beginner-friendly series with escalating control-flow obfuscation. The serial must be 11 characters long, start with `A`, have `X` at positions 4 and 8. Teaches you to recognize simple obfuscation patterns and trace character-position constraints.

**Key technique:** Recognising length and character-position constraints under basic control-flow obfuscation.

---

### 4. OldSoft's KeyGenMe #2 — by wolverine2k

|Field|Info|
|---|---|
|**Binary**|PE64|
|**Goal**|Write a keygen|
|**Techniques**|x64dbg, serial arithmetic, Python keygen|
|**Challenge**|https://crackmes.one/crackme/5c9e187b33c5d4419da55648|
|**Writeup**|https://crackmes.one/crackme/5c9e187b33c5d4419da55648 (solutions tab)|

**Description:** Serial is derived from the username using a formula: `prefix = 3*(L-1) + L` and `checksum = (L*(L+7))//2 + sum(ord chars)`. Use x64dbg to observe the serial being computed in `rbx`, then reverse the formula to write a Python keygen.

**Key technique:** Watching register values in a debugger to infer the keygen formula.

---

## ⚠️ INTERMEDIATE

---

### 5. crackme by raxer (Windows build)

|Field|Info|
|---|---|
|**Binary**|x64 PE|
|**Goal**|Find the password (no bytepatching)|
|**Techniques**|x64dbg, XOR loop analysis|
|**Challenge**|https://crackmes.one/crackme/5ed5b3c833c5d449d91ae6d0|
|**Writeup**|https://github.com/v0idMrK/CrackMe-challenge-writeup-1|

**Description:** The Windows variant of raxer's challenge. A character-by-character XOR loop validates the key against a reference string. You must understand the algorithm rather than patch a jump — a great forcing function for thorough analysis.

**Key technique:** XOR-based character comparison loop analysis; no-patch constraint forces full algorithm understanding.

---

### 6. Beginner Windows crackmes — x64dbg / x32dbg guide

|Field|Info|
|---|---|
|**Binary**|PE32 + PE64|
|**Goal**|Bypass authentication checks|
|**Techniques**|String references, conditional jump analysis, `GetDlgItemTextA`|
|**Challenge**|https://crackmes.one/|
|**Writeup**|https://www.linkedin.com/posts/talalalikhan_reverse-engineering-crackmes-activity-7364933106660732928-3pd5|

**Description:** Two challenges in one guide. A 64-bit challenge uses string references to pivot from a "Failed" branch to the "Success" branch. A 32-bit one traces `GetDlgItemTextA` and `lstrcmp` in a dialog-based app and analyses the `jne` controlling "Try again" vs "Good boy" output.

**Key technique:** String reference navigation in x64dbg; understanding dialog-based Windows app validation.

---

### 7. FatMike's CrackMe #1 — UPX + serial check

|Field|Info|
|---|---|
|**Binary**|PE32 (UPX packed)|
|**Goal**|Unpack and find valid serial|
|**Techniques**|CFF Explorer, UPX unpack, Ghidra, re-analysis|
|**Challenge**|https://crackmes.one/ (search "FatMike CrackMe 1")|
|**Writeup**|https://fewstreet.com/2024/10/22/reverse-engineering-crackme-with-ghidra.html|

**Description:** The binary is packed with UPX 2.90 — Ghidra only sees two sections (`UPX0` and `UPX1`) and can't find functions. Use CFF Explorer to confirm the packer, unpack with `upx -d`, re-import into Ghidra, then re-analyze to reveal `check_input` and the serial validation logic.

**Key technique:** Packer detection and unpacking workflow; re-analysis after unpacking in Ghidra.

---

### 8. Reverse Engineering CTF-writeup collection — johnnnathan

|Field|Info|
|---|---|
|**Binary**|Various Windows PE|
|**Goal**|Various — curated multi-challenge repo|
|**Techniques**|Mixed|
|**Challenge + Writeups**|https://github.com/johnnnathan/Crack|

**Description:** A GitHub repository solving one hard crackme per week from crackmes.one and crackmy.app. Each folder has a `solution.txt` walkthrough and a `keygen.py` where applicable. Good for reading different analysts' thought processes across a range of challenge types.

**Key technique:** Repository covers diverse techniques — use it as a reference after attempting each challenge yourself.

---

## 🔴 HARD

---

### 9. tuts4you Users Desktop Crackme

|Field|Info|
|---|---|
|**Binary**|x64 PE (multi-threaded)|
|**Goal**|Find the correct password|
|**Techniques**|VM obfuscation, anti-debug (HANDLE tricks), Frida, x64dbg Run Trace|
|**Challenge**|https://crackmes.one/|
|**Writeup**|https://github.com/extremecoders-re/tuts4you_users_desktop_crackme_writeup|

**Description:** A heavily protected binary with multiple anti-debug layers (HANDLE manipulation, thread-based protections) and full VM-based code obfuscation. Workflow: disable ASLR by patching the PE header, suspend the protection thread in Process Hacker, attach x64dbg, use "Run Trace" to log all instructions until `MessageBoxW`, filter the trace log for XOR instructions, then inject a Frida script that intercepts each XOR at `0x14004602B` to reconstruct the password character by character.

**Key technique:** Multi-thread suspension, run-trace logging, Frida instrumentation to defeat VM obfuscation.

---

### 10. FatMike's CrackMe #4 — packed, anti-debug, name/serial

|Field|Info|
|---|---|
|**Binary**|PE (custom packer, anti-debug)|
|**Goal**|Unpack, or write a loader; optionally write a keygen|
|**Techniques**|Custom unpacking, anti-debug bypass, reversed name/serial relationship|
|**Challenge**|https://crackmes.one/crackme/647cfb9633c5d4393891365b|
|**Writeup**|https://crackmes.one/crackme/647cfb9633c5d4393891365b (solutions tab)|

**Description:** The hardest in FatMike's series. Uses a custom packer (not standard UPX), includes multiple anti-debug tricks, and inverts the typical keygen relationship — the **name is generated from the serial**, not the other way around. Requires understanding the protection scheme before you can even reach the serial validation logic.

**Key technique:** Custom packer analysis, reversed name/serial dependency, anti-debug identification and bypass.

---

### 11. DLL MEGA HARD v3 — by ultrazvukoff

|Field|Info|
|---|---|
|**Binary**|PE (heavy obfuscation, custom packer)|
|**Goal**|Find the password or patch the program|
|**Techniques**|Advanced anti-debug, obfuscation, thread analysis|
|**Challenge**|https://crackmes.one/crackme/687bdf0baadb6eeafb399431|
|**Writeup**|No public solution yet — unsolved as of 2026|

**Description:** Described by its author as the most difficult crackme they have published. It uses `csrss.exe`-based message handling (bypassing ordinary `MessageBox`/`CreateWindow` hooks), a custom packer that prevents breakpoints inside threads, heavy code obfuscation with a runtime decoding mechanism, and dynamic function name resolution. No complete public solution exists yet — this is a challenge for experienced reversers.

**Key technique:** Thread-level anti-debug, process-external message handling, runtime function name decoding.

---

### 12. flcksr's CrackMe 2.0 — UPX + integrity checks

|Field|Info|
|---|---|
|**Binary**|PE64 (UPX packed + integrity checks)|
|**Goal**|Find valid key (patching also acceptable)|
|**Techniques**|UPX unpack, runtime debugging, integrity check bypass|
|**Challenge**|https://crackmes.one/crackme/66a0953690c4c2830c820e5a|
|**Writeup**|https://crackmes.one/crackme/66a0953690c4c2830c820e5a (solutions tab)|

**Description:** Packed with UPX, but the binary also implements self-integrity checks — simply running `upx -d` to unpack causes the program to refuse to run. You must use a runtime debugger to reach the key validation function, then either NOP the integrity check (`test al,al` → NOP) or fully reverse the key validation logic.

**Key technique:** Integrity-aware unpacking; understanding why static unpackers fail and why runtime debugging is necessary.

---

### 13. crackmes.one CTF 2026 — Windows challenges (official)

|Field|Info|
|---|---|
|**Binary**|Multiple PE formats|
|**Goal**|Various — CTF-grade|
|**Techniques**|Full suite|
|**Challenge + Writeups**|https://github.com/crackmesone/ctf-2026-challenges-public|

**Description:** The Windows entries in the official 2026 crackmes.one CTF. These are full competition-grade challenges with official writeups published post-event. They represent the ceiling of difficulty on the platform and use techniques drawn from real-world software protection schemes.

**Key technique:** Competition-grade — custom packers, anti-debug stacks, algorithm reversal, keygen writing.

---

---

## Learning Roadmap

```
START HERE
    │
    ▼
[Linux Easy]          keyg3nme → easy_reverse → PrettyDamnEasy
    │
    ▼
[Windows Easy]        find_the_pass → Baby Keygen series → OldSoft KeyGenMe
    │
    ▼
[Linux Intermediate]  Crackme-one (ltrace) → noprelo (anti-ptrace) → crackme05 (keygen)
    │
    ▼
[Windows Intermediate] FatMike #1 (UPX) → raxer crackme → FatMike #4 (custom packer)
    │
    ▼
[Linux Hard]          ioli 0x03-0x05 → Simple obfuscation → CTF 2026 Linux
    │
    ▼
[Windows Hard]        tuts4you Desktop → DLL MEGA HARD v3 → CTF 2026 Windows
```

---

## Tips & Notes

- Always work inside a **virtual machine**. Crackmes use the same techniques as malware (packers, anti-debug, self-modifying code).
- Install all **Visual C++ Redistributable** versions (2010–2022) in your Windows VM upfront to avoid dependency errors.
- Crackmes flagged by Windows Defender are almost always **false positives** — the protection techniques overlap with malware signatures.
- The platform zip password is always `crackmes.one` unless the challenge author specifies otherwise.
- Writeups must be detailed (not just the flag). Read others' writeups to learn methodology, not just answers.

---

## Useful Resources

|Resource|Link|
|---|---|
|crackmes.one main site|https://crackmes.one|
|crackmes.one FAQ|https://crackmes.one/faq|
|crackmes.one CTF 2026 public repo|https://github.com/crackmesone/ctf-2026-challenges-public|
|Multi-challenge writeup repo (johnnnathan)|https://github.com/johnnnathan/Crack|
|CTF writeup collection (JohnnyCurran)|https://github.com/JohnnyCurran/CTF-Writeups|
|Beginner series (Asm0d3us, Medium)|https://medium.com/@Asm0d3us/1-crackmes-one-beginner-friendly-reversing-challenges-6df94ea6b29d|
|Ghidra download|https://ghidra-sre.org|
|radare2 docs|https://rada.re/n/|
|x64dbg download|https://x64dbg.com|