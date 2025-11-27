# Lab 8 — 3-to-8 Decoder with Best EDP
### Cadence Virtuoso • Logical Effort • High-Speed Digital Design

This folder contains the complete implementation, simulation results, calculations, and analysis for **Lab 8: 3-to-8 Decoder with Best Energy–Delay Product (EDP)** as part of **EE4540L/6540L – VLSI Design Lab**.

---

## Objective
Design a **3-to-8 decoder** that meets the following goals:

- High operating frequency  
- Optimized propagation delays (tPLH, tPHL)  
- Minimum Energy–Delay Product (EDP)  
- Balanced rise/fall delays using Logical Effort  
- Performance comparison across multiple VDD values  

---

## Key Concepts Used
- Logical Effort (g, h, p, F = G × B × H)  
- Gate sizing (Cin = g × Cout / f)  
- Delay equalization (tPLH ≈ tPHL)  
- Maximum frequency extraction  
- Multi-VDD simulation and EDP analysis  
- CMOS delay & power trade-offs  

---

## Design Flow Summary
1. Calculated path effort and determined best number of stages  
2. Compared **1–4 stage** topologies  
3. Selected **3-stage architecture → INV → NAND3 → INV**  
4. Computed and applied transistor dimensions using logical effort  
5. Built the decoder schematic using custom-sized gates  
6. Simulated at VDD = 1V with exhaustive 3-bit input  
7. Extracted tPLH, tPHL, rise/fall time, power  
8. Resized transistors for delay balancing  
9. Determined **maximum operating frequency = 2 GHz**  
10. Simulated at multiple VDD (1.0 to 0.2 V)  
11. Computed EDP and identified best voltage  

---

## Final Gate Sizing Summary

| Gate | NMOS Width | PMOS Width |
|------|------------|------------|
| Inverter 1 | 100 nm | 150 nm |
| NAND3 | 610 nm each | 405 nm each |
| Inverter 2 | 990 nm | 1480 nm |

---

## Multi-VDD Summary

| VDD (V) | Max Frequency (GHz) | Avg Delay (ps) | Avg Power (µW) | EDP (fJ·s) |
|---------|----------------------|----------------|------------------|------------|
| **0.5** | 2 | 121.581 | 22.89 | **2.78 (Best)** |
| 0.8 | 2 | 61.54 | 70.03 | 4.31 |
| 0.9 | 2 | 57.67 | 98.67 | 5.69 |
| 1.0 | 2 | 55.51 | 138.6 | 7.70 |
| 0.2 | – | – | 0.2912 | – (Not functional) |

**✔ Best energy-efficiency achieved at 0.5 V**



