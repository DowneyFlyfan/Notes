---
id: Readme
aliases: []
tags: []
---

# Introduction

- This is a repo for my **Notes**.

# Temporary

- MIPS R10K: 1st Out-of-Order(OOO) Processor

- register map between L & P registers (Pick PR from **Free List**)

- logical(architectural) register file

- physical register file

- free list

- explicit register renaming (not read until execution) is register map

- active list / Reorder Buffer(ROB) (reorder instructions in IQ)

- n-wide Superscalar: n instructions in 1 cycle, **only way to make CPI < 1**

- issue puts instructions in buffer; dispatch sents instructions to functional units

- When Superscalar gets wider，bypass logic / register naming, number of ports, rescheduling complexity will **quadratic increase**

- Very Long Instruction Words (VLIW): Scheduling is done by compiler (Fixed number of instructions issued per cycle)

- Store/Load = Memory Reference

| Role/Area | Description |
|---|---|
| CAD Tooling | Develops CAD tools and integrates software. |
| RTL Hardware Acceleration | Accelerates hardware design and simulation at RTL. |
| Design for Test (DFT) | Designs testability features for manufacturing. |
| Hardware Design | Defines architecture and designs digital circuits. |
| Verification | Ensures functional correctness of hardware. |
| Implementation | Handles physical chip realization (synthesis, layout, timing). |

