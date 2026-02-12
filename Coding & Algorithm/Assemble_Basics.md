---
id: Assemble_Basics
aliases: []
tags:
  - Coding
---

# Basics

- Different Jmp

| Instruction | Name | Note | Speed | Instruction Length (bytes) |
| :--- | :--- | :--- | :--- | :--- |
| `jmp [rbx]` | Register indirect jump | through memory | slowest | 2 |
| `jmp rbx` | Register Direct Jump | | fast | 2 + 1(REX Prefix) |
| `jmp target` | Direct Jump | | fastest | 5 |

- `rax` is the content of `rax`, 

- `[rax]` is an equivalence of `*rax` in C, which means take the value of the address stored in `rax` (in this case, the value in `rax` is considered as an address)

- `align` is for memory padding

- `%+` for concatenation

- `eax (32-bits)` means **extended** part (last 32-bits) of `rax (64-bits)`

- `SECTION`: Indicate its mode(rwx), seperated in memory

- `%%` to make sure that the label is `unique` globally

- register structure

|----------------------- RCX (64 bits) -----------------------|
|                       |---------- ECX (32 bits) ------------|
|                       |           |----- CX (16 bits) ------|
|                       |           |-- CH (8) --|-- CL (8) --|

# x86-64

- L1 Cache Line: 64 bytes
