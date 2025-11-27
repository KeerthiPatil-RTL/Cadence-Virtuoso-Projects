# Lab 8 — 3-to-8 Decoder with Best EDP
### Cadence Virtuoso • Logical Effort • High-Speed Digital Design



## Objective
Design a **3-to-8 decoder** that meets the following goals:

- High operating frequency  
- Optimized propagation delays (tPLH, tPHL)  
- Minimum Energy–Delay Product (EDP)  
- Balanced rise/fall delays using Logical Effort  
- Performance comparison across multiple VDD values  



## Key Concepts Used
- Logical Effort (g, h, p, F = G × B × H)  
- Gate sizing (Cin = g × Cout / f)  
- Delay equalization (tPLH ≈ tPHL)  
- Maximum frequency extraction  
- Multi-VDD simulation and EDP analysis  
- CMOS delay & power trade-offs  



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



## Final Gate Sizing Summary

| Gate | NMOS Width | PMOS Width |
|------|------------|------------|
| Inverter 1 | 100 nm | 150 nm |
| NAND3 | 610 nm each | 405 nm each |
| Inverter 2 | 990 nm | 1480 nm |


## Multi-VDD Summary

| VDD (V) | Max Frequency (GHz) | Avg Delay (ps) | Avg Power (µW) | EDP (fJ·s) |
|---------|----------------------|----------------|------------------|------------|
| **0.5** | 2 | 121.581 | 22.89 | **2.78 (Best)** |
| 0.8 | 2 | 61.54 | 70.03 | 4.31 |
| 0.9 | 2 | 57.67 | 98.67 | 5.69 |
| 1.0 | 2 | 55.51 | 138.6 | 7.70 |
| 0.2 | – | – | 0.2912 | – (Not functional) |

**✔ Best energy-efficiency achieved at 0.5 V**


#  RESULTS
- The logical-effort–based 3-stage design (**INV → NAND3 → INV**) produced the **lowest delay (17.15)** among all tested options.  
- The decoder successfully generated **correct one-hot outputs** for all input combinations.  
- After resizing, **tPLH and tPHL became closely matched**, improving timing symmetry.  
- The design operated reliably up to **2 GHz** at VDD = 1V.  
- Multi-VDD simulations revealed significant power savings at lower VDD, with **0.5V achieving the lowest EDP**.  
- At **0.2V** the circuit failed to switch (only leakage), confirming the minimum usable voltage limit.



#  ANALYSIS
- Logical Effort accurately identified the optimal stage count and gate arrangement.  
- The 3-stage architecture minimized delay by balancing electrical and logical efforts.  
- Transistor width adjustments had a major impact on rising vs. falling delays.  
- Delay decreased with increasing VDD, but power increased **quadratically**, making high-VDD operation less energy efficient.  
- **EDP evaluation showed 0.5V provides the best balance between speed and power**, despite having higher delay than 1V.  
- The failure at 0.2V aligns with MOSFET threshold behavior and insufficient drive strength.



#  CONCLUSION
The 3-to-8 decoder was successfully designed, optimized, and analyzed using **Logical Effort theory** and Cadence Virtuoso simulations.  
The final design achieved:

- Correct functional decoding  
- Balanced propagation delays  
- Maximum frequency of **2 GHz**  
- Best energy efficiency at **0.5V**  
- Clear validation of CMOS voltage–delay–power trade-offs  


