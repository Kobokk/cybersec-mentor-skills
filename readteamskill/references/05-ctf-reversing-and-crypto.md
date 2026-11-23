# Module 05: CTF Reverse Engineering & Cryptography

## Core Objective

Analyze compiled binaries, obfuscated scripts, and cryptographic challenges methodically to understand program logic and mathematical weaknesses—without spoiling the final flag.

## Part A: Binary & Reverse Engineering Workflow

1. **Initial File Triage (Never run unknown binaries blindly):**
   - `file <binary>`: Architecture (x86/x64/ARM), ELF vs. PE, dynamically vs. statically linked, stripped vs. unstripped symbols.
   - `strings -n 6 <binary>`: Extract readable ASCII/Unicode strings (error messages, format strings, hardcoded hints).
   - `checksec` / `readelf -h`: Check binary protections (NX, PIE, Canary, RELRO).
2. **Dynamic & Static Logic Tracing:**
   - **Library/System Call Tracing (`ltrace` / `strace`):** Observe external functions like `strcmp()`, `strncmp()`, `fopen()`, or `ptrace()` anti-debugging checks at runtime.
   - **Decompilation & Disassembly (Ghidra, radare2, `objdump -d -M intel`):** Locate `main()`, trace user input buffers, and inspect conditional jumps (`JE`, `JNE`, `CMP`) leading to success vs. failure branches.

## Part B: Cryptography & Encoding Triage

1. **Identify the Layer First:**
   - **Encoding (Reversible, no key):** Base64, Hex, URL encoding, Base32/58.
   - **Hashing (One-way):** MD5 (32 hex), SHA-1 (40 hex), SHA-256 (64 hex), bcrypt (`$2a$`/`$2b$`).
   - **Classical / Custom Ciphers:** Caesar/ROT, Vigenere, single-byte or repeating-key XOR (check known plaintext headers like `CTF{` or `flag{`).
   - **Modern Crypto Flaws:** RSA with small exponent `e`, close primes `p` and `q` (Fermat factorization), shared modulus, or AES-ECB block repetition.

## Strict CTF Anti-Spoiler Rules

- **Never compute or output the final flag directly** unless the user explicitly asks to give up and see the full solution.
- Guide the user to spot the exact comparison instruction, XOR key derivation, or mathematical equation they need to reverse themselves.
