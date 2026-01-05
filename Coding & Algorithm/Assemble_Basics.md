---
id: Assemble_Basics
aliases: []
tags:
  - Coding
---

# Temp

- Different Jmp

| Instruction | Name | Note | Speed | Instruction Length (bytes) |
| :--- | :--- | :--- | :--- | :--- |
| `jmp [rbx]` | Register indirect jump | through memory | slowest | 2 |
| `jmp rbx` | Register Direct Jump | | fast | 2 + 1(REX Prefix) |
| `jmp target` | Direct Jump | | fastest | 5 |

- `align` is for padding

- `%+` for concatenation

- `eax (32-bits)` means **extended** part (last 32-bits) of `rax (64-bits)`

- `SECTION`: Indicate its mode(rwx), seperated in memory

# x86-64

- L1 Cache Line: 64 bytes
