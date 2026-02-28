---
id: Paralellism
aliases: []
tags:
  - Comp_Arch
---

# Pipeline

## How Deep?

### Why can't Pipeline be so deep

| Symbol | Description |
|--------|-------------|
| $T_1$ | Input time of the first signal |
| $T_2$ | Input time of the consecutive second signal |
| $T_L$ | Additional time caused by Clock Distribution Network and Clock Skew |
| $T_M$ | Time for Maximum Path |
| $T_m$ | Time for Minimum Path |

$$
\begin{equation}
\begin{aligned}
T_2 + T_m &\gt T_1  + T_M + T_L \\
T_{clock} &= T_2 - T_1 \gt T_M - T_m + T_L
\end{aligned}
\end{equation}
$$

- Balance Different Path can reduce $T_M - T_m$

### How deep ?

| Symbol | Description |
|--------|-------------|
| $C$ | Total cost of the pipeline |
| $P$ | Performance (throughput) of the pipeline |
| $G$ | Fixed cost per pipeline stage |
| $L$ | Latency overhead per pipeline stage |
| $k$ | Number of pipeline stages (depth) |
| $T$ | Total execution time without pipelining |
| $S$ | Setup time overhead per stage |
| $k_{opt}$ | Optimal number of pipeline stages that minimizes cost per performance |

# Instruction Level Parallelism

> A Classic RISC-V Arch

![](./imgs/Parallelism/RISC-V_Basic_Pipeline.png)

## Classic 5-Level Pipeline

> IF(Instruction Fetch) -> ID(Instruction Decode) -> ***OF(Operand Fetch)*** -> EX(Execution) -> ***MEM(Memory Access)*** -> WB(Write Back)

- OF can be done in parallel with ID; MEM can be done in EX Stage

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

# Key Formulas

$$
\begin{equation}
\begin{aligned}
\text{Throughput}  &= \text{Number of Tasks processed per Unit Time}  \\
\end{aligned}
\end{equation}
- [ ] $$
