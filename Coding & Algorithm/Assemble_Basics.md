---
id: Assemble_Basics
aliases: []
tags:
  - Coding
---

# Basics

## Different Jmp

| Instruction | Name | Note | Speed | Instruction Length (bytes) |
| :--- | :--- | :--- | :--- | :--- |
| `jmp [rbx]` | Register indirect jump | through memory | slowest | 2 |
| `jmp rbx` | Register Direct Jump | | fast | 2 + 1(REX Prefix) |
| `jmp target` | Direct Jump | | fastest | 5 |

## register structures

|----------------------- RCX (64 bits) -----------------------|
|                       |---------- ECX (32 bits) ------------|
|                       |           |----- CX (16 bits) ------|
|                       |           |-- CH (8) --|-- CL (8) --|
|----------------------- RSI (64 bits) -----------------------|
|                       |---------- ESI (32 bits) ------------|
|                       |           |----- SI (16 bits) ------|
|----------------------- R8 (64 bits) ------------------------|
|                       |---------- R8D (32 bits) ------------|
|                       |           |----- R8W (16 bits) -----|
|                       |           |-- R8B (8) --|

## Memory Address

$$
\begin{equation}
\begin{aligned}
\text{Effective Address} &= \text{Base} + \text{Index} \times 2^{\text{Scale}} + \text{Displacement} 
\end{aligned}
\end{equation}
$$

## Others

- `rax` is the content of `rax`

- `[rax]` is an equivalence of `*rax` in C, which means take the value of the address stored in `rax` (in this case, the value in `rax` is considered as an address)

- `%+` for concatenation

- `SECTION`: Indicate its mode(rwx), seperated in memory

- `%%` to make sure that the label is `unique` globally

# x86-64

## IA-32 Modes

Operating Mode: Real Mode, protected mode, virtual 8086 mode(run dos program)
Compatability Mode: Run 32-bit program

- L1 Cache Line: 64 bytes
