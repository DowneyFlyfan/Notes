---
id: Basic_Circuits
aliases: []
tags: []
---

# Combinational Logic Circuits

## TriState Buffer

- **Enable**的时候是正常buffer, **Not Enable**的时候输出为$Z$

![](./imgs/Combinational_Logic/tristate-buffer.png)

## Multiplexer

### 2-1 MUX

- RTL电路 和 Truth Table

![](./imgs/Combinational_Logic/mux.png)

- 门级电路

![](./imgs/Combinational_Logic/mux-gate.png)

- 用TriState Buffer实现MUX

![](./imgs/Combinational_Logic/mux-tristate-buffer.png)

# Latch & Flip-Flops

## Latches

### Inverter Latch

- 只有输出，没有输入, 实用性比较差

![](./imgs/Sequential_Logic/Inverter-Latch.png)

### SR-Latch

- 能正常锁存，但是当**Set**和**Reset**都为1的时候输出全是0(**不合理了**)

![](./imgs/Sequential_Logic/SR-Latch-Circuit.png)

![](./imgs/Sequential_Logic/SR-Latch-TruthTable.png)

### D-Latch

- 在时钟正周期，只要数据改变，输出就立刻改变

![](./imgs/Sequential_Logic/D-Latch.png)

## Flip-Flops(FF)

### D-FFs

- 通过在时钟**负周期存数据，正周期传数据**，实现了**只在时钟上升沿改变数据**

![](./imgs/Sequential_Logic/D-Flip-Flops.png)

### Register

- 多个**D-Flip-Flops**共享一个**Clock**

![](./imgs/Sequential_Logic/Register.png)

### Enabled-FFs

- 最好不用*Scematic (b)*, 因为**时钟一般不与门相连**

![](./imgs/Sequential_Logic/Enable-FF.png)

### Resettable FFs

- 这是一个时钟同步的**FF**

- 异步的**D**与**Q**同步变化

![](./imgs/Sequential_Logic/Resettable-FF.png)

# Adder

- 所有的$t_{FA}$指的都是**Single-Bit FA**的时间

## Simple Adders

1. Half Adder

![](./imgs/Adders/Half_Adder.png)

Ripple Carry Adder (RCA)

2. Full Adder

![](./imgs/Adders/Full_Adder.png)

3. Ripple Carry Adder

$$
\begin{equation}
\begin{aligned}
t_{ripple} &= t_{FA}
\end{aligned}
\end{equation}
$$

![](./imgs/Adders/Ripple_Carry_Adder.png)

## Carry-Propogate Adder (CPA)

![](./imgs/Adders/Carry_Propogate_Adder.png)

### Carry-Lookahead Adder (CLA)

![](./imgs/Adders/CLA.png)

1. 定义

- **Propogate**: 有$C_{in}$情况输出$C_{out}$

- **Generate**: 不管有没有$C_{in}$都输出$C_{out}$

2. 单位加法的进位计算

$$
\begin{equation}
\begin{aligned}
P_i &= A_i + B_i \\
G_i &= A_i B_i \\
C_i &= G_i + P_i C_{i-1}
\end{aligned}
\end{equation}
$$

3. Block加法的进位计算(**4-bits为例**)

- 此时的$C_{in}$ 和 $C_{out}$是针对块而言的，**中间的不算**

$$
\begin{equation}
\begin{aligned}
P_{3:0} &= P_3P_2P_1P_0 \\
G_{3:0} &= G_3 + P_3(G_2 + P_2 (G_1 + P_1 G_0)) \\
C_i &= P_{i:j} + P_{i:j} C_{j}
\end{aligned}
\end{equation}
$$

4. 总时间

- 先算完所有**块之间的进位**，再在**块内部算Sum**

$$
\begin{equation}
\begin{aligned}
t_{CLA} &= t_{pg} + t_{pg\_blocks} +  (\frac{N}{k} - 1) t_{Logic} + kt_{FA}
\end{aligned}
\end{equation}
$$

### Prefix Adder

![](./imgs/Adders/Prefix_Adder.png)

1. **核心: 加一个$-1$位，使得整个模块的$P_{in} = 0, P_{out}=0$; 这样利用$G$可以直接获得$C$**

2. 计算方式

$$
\begin{equation}
\begin{aligned}
P_{-1} &= 0 \\
G_{-1} &= C_{in} \\
C_{i-1} &= G_{i-1:-1} \\
S &= A \oplus B \oplus C_{i-1}
\end{aligned}
\end{equation}
$$

3. 总时间

$$
\begin{equation}
\begin{aligned}
t &= t_{pg} + t_{XOR} + \log_2 N \  t_{black\_cell} \\
\end{aligned}
\end{equation}
$$

## Carry-Save Adder (For 3 Addings)

![](./imgs/Adders/Carry_Save_Adder.png)

- 3个数加减变成2个数加减, 然后用普通Adder搞定

$$
\begin{equation}
\begin{aligned}
S_i &= A_i \oplus B_i \oplus C_i \\
C_{i+1} &= A_i B_i + A_i C_i + B_i C_i
\end{aligned}
\end{equation}
$$

# Divider
