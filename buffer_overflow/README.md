# Buffer Overflow Lab

This project demonstrates a classic **stack-based buffer overflow** attack. It was developed as part of a hands-on lab for the course **Hacking Techniques**, where students were provided with base code and tasked with crafting a working exploit.

---

## 🧠 Objective

To understand and exploit a buffer overflow vulnerability by:

- Injecting shellcode into a vulnerable program.
- Overwriting the return address to redirect execution.
- Gaining a shell (`/bin/sh`) upon successful exploitation.

---

## 📄 Files Included

- `stack.c`: Vulnerable C program that reads input from `badfile` and copies it unsafely into a local buffer.
- `exploit.c`: C program that generates a `badfile` with shellcode and a guessed return address.
- `call_shellcode.c`: Tests if the shellcode works in isolation.
- `simple_shellcode.c`: Minimal program that spawns a shell using `execve`.

---

## ⚙️ Compilation & Setup

### 1. Disable ASLR (temporarily)

```bash
echo 0 | sudo tee /proc/sys/kernel/randomize_va_space
```

### 2. Compile the vulnerable program

```bash
gcc -fno-stack-protector -z execstack -no-pie -o stack stack.c
```

### 3. Generate the exploit

```bash
gcc -o exploit exploit.c
./exploit
```

### 4. Run the vulnerable program

```bash
./stack
```

If successful, you should get a shell.

---

## 🧪 Notes

- You may need to adjust the return address and offset in `exploit.c` depending on your system.
- Use `gdb` to inspect the stack and find the correct address:
  ```bash
  gdb ./stack
  (gdb) break bof
  (gdb) run
  (gdb) info frame
  (gdb) x/40x $esp
  ```

---

## ⚠️ Disclaimer

This code is for **educational purposes only**. Do not use it on systems you do not own or have explicit permission to test.

