---
id: Paralellism
aliases: []
tags:
  - Comp_Arch
---

# Instruction Level Parallelism

![](./imgs/Parallelism/RISC-V_Basic_Pipeline.png)

```cpp

```

## Typical 5-Level Pipeline

IF(Instruction Fetch)

### Problems

> Data Hazard (RAW,WAR,WAW) caused by data dependency

- Use Bypass(Forward) to solve data dependency problem

![](./imgs/Parallelism/Forward_Pipeline.png)

- Sometimes, Forward is not enough. Need **Pipeline-Interclock** to stall the pipeline

![](./imgs/Parallelism/Pipeline-Interclock.png)

> Branch Hazard

# Others

Load-Store: Only Load and Store can access memory (ARM, RISC-V)

Register-Memory: Can use both register value and memory in same instruction
