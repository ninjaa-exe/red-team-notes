# Buffer Overflow

A buffer overflow occurs when a program writes more data to a buffer than it can hold.

This can overwrite adjacent memory and potentially allow an attacker to control the program's execution flow.

Buffer overflows are common in programs written in low-level languages such as:

- C
- C++

These languages do not perform automatic bounds checking.

---

# Basic Example

Consider the following C program:

```c
#include <stdio.h>
#include <string.h>

int main() {
    char buffer[8];
    gets(buffer);
    printf("You entered: %s\n", buffer);
    return 0;
}
```

If the user enters more than 8 bytes, the extra data may overwrite memory beyond the buffer.

Example input: ``` AAAAAAAAAAAAAAAA ```

This may overwrite adjacent memory and crash the program.

---

# Stack-Based Buffer Overflow

Stack-based buffer overflows occur when data overwrites memory on the program stack.

Typical memory layout:

```
| Local Variables |
| Saved Frame Pointer |
| Return Address |
```

If the return address is overwritten, an attacker may redirect execution to arbitrary code.

# Exploitation Concept

In a typical buffer overflow attack, an attacker:

1. Sends input larger than the buffer

2. Overwrites the return address

3. Redirects execution to attacker-controlled code

Example payload structure: ``` [padding][return address][shellcode] ```

---

# Detecting Buffer Overflows

Indicators may include:

- program crashes

- segmentation faults

- abnormal application behavior

Testing may involve sending large or unexpected inputs to the program.

Example: ```bash python3 -c "print('A'*200)" ```

---

# Common Protections

Modern systems implement protections to mitigate buffer overflow attacks.

Examples include:

- ASLR (Address Space Layout Randomization)

- DEP / NX (Data Execution Prevention)

- Stack canaries

- Safe libraries

These protections make exploitation more difficult but not always impossible.

---

# Prevention

Secure coding practices can prevent buffer overflows.

Common techniques include:

- validating input length

- using safer functions

- implementing bounds checking

Example safer alternative: ```c fgets(buffer, sizeof(buffer), stdin); ```

Avoid unsafe functions such as:

- gets

- strcpy

- strcat

---

# Notes

Buffer overflow vulnerabilities have historically been responsible for many critical security flaws.

Understanding memory management and program execution is essential when studying these vulnerabilities.

Always perform testing only in **authorized environments.**