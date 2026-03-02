---
id: Branch_Predictor
aliases: []
tags: []
---

# TAGE (TAGged Geometric-Length) Predictor

> Geometric History Length of Partial Tables

- **Intuition**: Close History matters. Importance of long history decade in a geometric way

| Hash Function | Description |
|---------------|-------------|
| GF($2^8$) Multiplication | |
| Folded XOR | |
| Mod | |
| Bit Permutation | |

# BTB - A Simple Scenario

## Prediction

> BTB and BHB used for Simple Branch Prediction

![](./imgs/BPU/Morden_BTB_Mechanism.png)

- Vaddr: Virtual Address of the branch instruction, can be considered as pc

- BHB(Branch History Buffer): Branch Addresses are hashed ($f_3$) and stored in BHB

- BTB(Branch Target Buffer): The **Cache structure** on the left side

## Update

- Simply taking lower bits of PC and seperate them into target, tag, offset parts;

- Note that, BTB also has **more bits** for Core ID, Branch Type, Previlege Level etc.

# IBP - Indirect Branch Predictor

> A Tage Like Structure that replaces **taken counter** into a **full branch target**
