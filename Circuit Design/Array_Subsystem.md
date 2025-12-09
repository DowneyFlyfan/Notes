---
id: Array_Subsystem
aliases: []
tags:
  - Circuit
---

# SRAM

## Basic Cell

![](./imgs/Array_Subsystem/6T_SRAM_Cell.png)

### Read

1. Circuit and DC Transfer

![](./imgs/Array_Subsystem/SRAM_Read_Operation.png)



2. Column Read

![](./imgs/Array_Subsystem/SRAM_Column_Read.png)

### Write

1. DC Transfer

![](./imgs/Array_Subsystem/SRAM_Write_Oepration.png)

2. Column Write

![](./imgs/Array_Subsystem/SRAM_Column_Write.png)

### Cell Stability

#### Concepts

| Concept       | Condition/Description                                           |
|---------------|-----------------------------------------------------------------|
| Readability   | $D_1$ must be stronger than $A_1$ to pull it down               |
| Writability   | $A_2$ must be stronger than $P_2$ to pull it down               |
| P:A:N Ratio   | 1:2:4                                                           |
| Hold Margin   | Reduce $V_{DD}, V_t$ helps reduces hold margin                  |
| Read Margin   | Increase $V_{DD}, V_t$, reduce word line voltage helps reduces read margin |
| Write Margin  | Write margin is opposite of read margin                         |


#### Margins

> Hold Margin

![](./imgs/Array_Subsystem/SRAM_Hold_Margin.png)


> Read Margin

![](./imgs/Array_Subsystem/SRAM_Read_Margin.png)

> Write Margin

![](./imgs/Array_Subsystem/SRAM_Write_Margin.png)

## Decoder

- Simple Decoder

![](./imgs/Array_Subsystem/Simple_Decoders.png)

- Predecoder to reduce area

![](./imgs/Array_Subsystem/Predecoding_Circuit.png)

## Row Redundancy

![](./imgs/Array_Subsystem/Row_Redundancy.png)
