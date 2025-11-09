

Here's a concise explanation of common AV features, highlighting main implementation points:

- **Scanner:** Examines files, processes, and network traffic for threats.
    - **Main Implementations:** Real-time (on-access), on-demand, scheduled scans; varying speed and thoroughness.
- **Detection Techniques:** Methods to identify malware.
    - **Main Implementations:**
        - **Signature-based:** Matches known malware patterns (signatures).
        - **Heuristic-based:** Detects suspicious behavior or characteristics, even for new threats.
        - **Machine Learning/AI:** Uses learned patterns for advanced, adaptive detection.
        - **Cloud-based:** Leverages cloud for rapid analysis and threat intelligence.
- **Compressors and Archives:** Ability to scan inside compressed files (ZIP, RAR, etc.) where malware often hides.
    - **Main Implementations:** Support for various formats; recursive scanning; handling password-protected archives.
- **Unpackers:** Decrypts and decompresses "packed" or "obfuscated" malware code.
    - **Main Implementations:** Support for diverse packers; runtime unpacking in memory; de-obfuscation techniques.
- **Emulators:** Safely runs suspicious code in a virtual environment to observe its malicious behavior without harming the real system.
    - **Main Implementations:** Behavioral analysis; evasion detection; support for unpacking and script emulation.
