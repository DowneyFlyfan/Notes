---
id: Number_System
aliases: []
tags:
  - Circuit
---

# Number System

## Integars

1. Number System: 在任一数制中，每一个数位上允许使用的记数符号的个数被称为该数制的Base

- 每1位都对应1个表示该位在数码中的位置的值，这个值就称为数位的权值W
    
2. 扩展(在**verilog**中直接用`signed'()`来实现)

-对于无符号数，直接补0

-对于有符号数，直接补MSB (Maximum Significant Bit), 这叫做符号位扩展(Sign Extension)，方便进行运算

## Floating Numbers

| Type            | Formula                     | Sign Bit (s) | Mantissa (M), 有效位 | Exponent (E) | Exponent Bias |
| :-------------- | :-------------------------- | :----------- | :----------- | :----------- | :------------ |
| Single-Floating | $(-1)^s \times 1.M \times 2^{E-127}$ | 1            | 23           | 8            | 127           |
| Double-Floating | $(-1)^s \times 1.M \times 2^{E-1023}$ | 1            | 52           | 11           | 1023          |
