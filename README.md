# Hacking Techniques Labs

This repository showcases two hands-on projects focused on **low-level system exploitation**, demonstrating practical knowledge of memory corruption vulnerabilities and CPU-level side-channel attacks. These projects were developed to deepen understanding of how real-world attacks are constructed and executed, and to demonstrate proficiency in C programming, memory layout analysis, and bypassing modern security mechanisms.

---

## 🔐 Projects Included

### `spectre-meltdown-lab/`
A complete implementation of **Spectre** and **Meltdown** attacks, including:

- A custom Linux kernel module that exposes secret data via `/proc`.
- User-space programs that implement:
  - **Flush+Reload** cache timing technique.
  - **Meltdown** attack using speculative execution to read privileged memory.
  - **Spectre** attack exploiting branch prediction to leak secrets.
- Multiple variants of each attack, including improved versions with scoring and repetition for accuracy.

This project demonstrates:
- Deep understanding of CPU microarchitecture.
- Ability to manipulate speculative execution paths.
- Use of low-level timing instructions (`rdtscp`, `clflush`) and signal handling.

---

### `buffer-overflow-lab/`
A classic **stack-based buffer overflow** exploit chain, including:

- A vulnerable C program (`stack.c`) with an unsafe `strcpy()` call.
- Exploit written in C that:
  - Injects shellcode into memory.
  - Overwrites the return address to redirect execution.
  - Spawns a shell (`/bin/sh`) upon success.
- Shellcode testing programs and manual return address calculation.

This project demonstrates:
- Manual memory layout analysis using `gdb`.
- Shellcode injection and NOP sled construction.
- Bypassing stack protections (e.g., disabling ASLR, stack canaries).

---

## 🛠️ Technical Highlights
- Written entirely in **C**.
- Exploits crafted for **x86 Linux** environments.
- Demonstrates knowledge of:
  - Stack frames and calling conventions.
  - Kernel module development.
  - CPU cache behavior and speculative execution.
  - Manual exploit development and debugging.

---

## ⚠️ Legal & Ethical Notice

All code in this repository is intended **strictly for demonstration and educational purposes** in controlled environments (e.g., virtual machines). These techniques must **never** be used on systems without explicit authorization.

---

## 💡 Want to Know More?

Each subfolder contains its own `README.md` with detailed explanations, compilation instructions, and execution steps.



