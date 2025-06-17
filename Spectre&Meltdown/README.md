# Spectre and Meltdown Attack Lab

This repository contains the source code and instructions to perform side-channel attacks known as **Spectre** and **Meltdown**. This project was developed as part of the **Hacking Techniques** course, where base code was provided to carry out practical exercises and understand how these low-level attacks work.

---

## 📁 Project Structure

The project is organized into the following folders:

- **`kernel_module/`**: Contains the kernel module required for the Meltdown attack.
- **`meltdown/`**: User-space programs implementing Meltdown attack variants.
- **`spectre/`**: User-space programs implementing Spectre attack variants.
- **`utils/`**: Auxiliary utilities for cache timing, exception handling, etc.

---

## 📂 Folder Contents

### `kernel_module/`
- `MeltdownKernel.c`: Kernel module source code that exposes secret data via `/proc/secret_data`.
- `Makefile`: Script to compile the module using kernel build tools.
- `.gitignore`: Prevents uploading auto-generated build files.

### `meltdown/`
- `MeltdownExperiment.c`: Basic demonstration of the Meltdown attack.
- `MeltdownAttack.c`: More robust and accurate version of the attack.

### `spectre/`
- `SpectreExperiment.c`: Basic demonstration of the Spectre attack.
- `SpectreAttack.c`: Initial implementation of the attack.
- `SpectreAttackImproved.c`: Improved version with repetition and scoring.

### `utils/`
- `CacheTime.c`: Measures memory access times to detect cache hits.
- `ExceptionHandling.c`: Handles segmentation faults using signals.
- `FlushReload.c`: Basic implementation of the Flush+Reload technique.

---

## ⚙️ Compilation and Execution Instructions

### Kernel Module

```bash
cd kernel_module/
make
sudo insmod MeltdownKernel.ko
dmesg | tail  # Check the secret's memory address
cat /proc/secret_data
sudo rmmod MeltdownKernel
```

### User-Space Programs

```bash
gcc -o attack attack.c
./attack
```

> Replace `attack.c` with the file you want to run (e.g., `MeltdownAttack.c`, `SpectreAttackImproved.c`, etc.).

---

## ⚠️ Disclaimer

These programs are intended **for educational purposes only** and should be executed in **controlled environments** (virtual machines or lab systems). They must not be used on production systems or against unauthorized targets.

