---
id: Circuit_Analysis
aliases: []
tags:
  - Circuit
---

# Basic Concept

- SPICE (Simulation Program with Integrated Circuits Emphasize) Model

# Typical Instances

1. Analyze a traditional inverter


| Parameter | Description | Notes |
|---|---|---|
| $t_{pdr}$ | propagate delay rise time | from input 0.5V to output 0.5V|
| $t_{pdf}$ | propagate delay fall time | from output 0.5V to input 0.5V|
| $t_{pd}$ | propagate delay time |$t_{pd} = \dfrac{t_{pdr} + t_{pdf}}{2}$ |
| $t_{rt}$ | rising time | between 0.2V - 0.8V|
| $t_{ft}$ | falling time |between 0.8V - 0.2V  |
