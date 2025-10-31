# Lab 5 – 4-Bit Adder/Subtractor Design Using Standard and Compound Gates

## 1. Objective
The main objective of this lab was to design and simulate a **4-bit Adder/Subtractor** circuit using a **hierarchical and modular** design approach in **Cadence Virtuoso (FreePDK45 – 45 nm CMOS)**.  
The design process began with a **1-bit Full Adder**, implemented using **NAND** and **XOR** gates, which served as the building block for the 4-bit ripple-carry system.  
The experiment also aimed to:
- Measure rising and falling propagation delays, and calculate average delay.  
- Evaluate **average power consumption** for various sizing cases.  
- Perform **transistor width adjustments** to achieve nearly equal rising and falling delays.  
- Demonstrate how standard-cell designs scale into larger arithmetic circuits.



## 2. Procedure
1. **Design of 1-Bit Full Adder:**  
   Derived Boolean equations for **Sum (S)** and **Carry (Cout)** using the truth table and K-map. Implemented the design using NAND and XOR gates.  

2. **Symbol Creation:**  
   Generated symbol view for hierarchical use in 4-bit design.  

3. **4-Bit Adder/Subtractor Construction:**  
   Four 1-bit full adders were connected in **ripple-carry** configuration. The carry-out of each stage was linked to the carry-in of the next.  

4. **Subtraction Mode Implementation:**  
   XOR gates were added to the **B** inputs, controlled by **Cin** (mode select).  
   - **Cin = 0 → Addition**  
   - **Cin = 1 → Subtraction**  

5. **Stimulus Setup:**  
   Applied pulse voltage sources for A and B inputs to test multiple binary combinations.  

6. **Simulation:**  
   Used **ADE Explorer** for transient simulations. Verified correct output for all combinations.  

7. **Delay Measurement:**  
   Measured **tpLH**, **tpHL**, and average delay for each SUM and COUT output.  

8. **Power Analysis:**  
   Computed average power using transient simulation results.  

9. **Transistor Resizing:**  
   Adjusted PMOS/NMOS widths to balance tpLH ≈ tpHL for each SUM and COUT node.  

10. **Documentation:**  
    Tabulated all propagation delay and power results before and after resizing for both **standard** and **compound** gate designs.



## 3. Simulation Results

### 1-Bit Full Adder – Standard Gate (W = 100 nm)
| Output | tpLH (ps) | tpHL (ps) | tavg (ps) | Power (µW) |
|:--|--:|--:|--:|--:|
| SUM | 20.44 | 21.78 | 21.11 | 6.62 |
| COUT | 13.11 | 11.63 | 12.37 | 6.62 |

**After Resizing:**  
SUM ≈ 22.60 ps, COUT ≈ 28.44 ps, Power = 15.29 µW  



### 1-Bit Full Adder – Compound Gate (W = 100 nm)
| Output | tpLH (ps) | tpHL (ps) | tavg (ps) | Power (µW) |
|:--|--:|--:|--:|--:|
| SUM | 13.02 | 14.94 | 13.98 | 5.99 |
| COUT | 13.06 | 10.90 | 11.98 | 5.99 |

**After Resizing:**  
SUM ≈ 14.45 ps, COUT ≈ 11.82 ps, Power = 6.11 µW  



### 4-Bit Adder/Subtractor – Standard Gate (W = 100 nm)
| Node | trise (ps) | tfall (ps) | tavg (ps) | Power (µW) |
|:--:|--:|--:|--:|--:|
| SUM0 | 36.06 | 38.05 | 37.06 | 17.83 |
| SUM1 | 51.67 | 44.90 | 48.29 | 17.83 |
| SUM2 | 52.07 | 44.90 | 48.49 | 17.83 |
| SUM3 | 64.65 | 70.62 | 67.63 | 17.83 |
| COUT | 80.57 | 76.75 | 78.66 | 17.83 |

**After Resizing:**  
SUM0–SUM3 ≈ 37–68 ps, COUT ≈ 77 ps, Power ≈ 17.95 µW  



### 4-Bit Adder/Subtractor – Compound Gate (W = 100 nm)
| Node | trise (ps) | tfall (ps) | tavg (ps) | Power (µW) |
|:--:|--:|--:|--:|--:|
| SUM0 | 54.58 | 47.49 | 51.03 | 17.95 |
| SUM1 | 55.15 | 47.47 | 51.31 | 17.95 |
| SUM2 | 42.37 | 48.57 | 45.47 | 17.95 |
| SUM3 | 81.36 | 87.67 | 84.52 | 17.95 |
| COUT | 51.85 | 53.44 | 52.65 | 17.95 |

**After Resizing:**  
SUM0–SUM3 ≈ 45–87 ps, COUT ≈ 51.8 ps, Power ≈ 17.74 µW  



### Transistor Width Adjustments
| Gate | PMOS (nm) | NMOS (nm) | Notes |
|:--|:--:|:--:|:--|
| XOR (Standard) | 165 | 720 | Balanced SUM path |
| NAND3 (Standard) | 250 | 110 | Carry path tuning |
| XOR (Compound) | 105 | 90 | Equal tpLH ≈ tpHL |
| NAND2 (Compound) | 135 | 90 | Carry optimization |



### Design Challenge
One of the major challenges in this lab was **transistor width balancing**.  
Adjusting the width for one output (e.g., SUM0) affected timing of others (SUM2, SUM3, COUT). Multiple iterations were required to achieve a good global balance.  
This demonstrated how **small geometry changes** can significantly influence overall delay and circuit performance.


## 4. Result
**Functionality:**  
All simulated vectors for both 1-bit and 4-bit designs matched theoretical results for addition (Cin = 0) and subtraction (Cin = 1).  

**Timing:**  
- Compound-gate full adder achieved **lower delay** than the standard-gate design.  
- In 4-bit circuits, delay increased from SUM0 → SUM3 → COUT due to ripple-carry propagation.  
- Resizing improved delay uniformity and balanced rising/falling transitions.  

**Power:**  
Slight power increase occurred after resizing, but compound gates maintained slightly lower power than standard gates.  


## 5. Conclusion
A **4-bit Adder/Subtractor** was successfully designed and verified using **Cadence Virtuoso (FreePDK45)**.  
The compound-gate design demonstrated **reduced propagation delay** while maintaining comparable power efficiency.  
Transistor resizing balanced tpLH ≈ tpHL for stable operation.  
In the 4-bit ripple-carry adder, delay growth toward higher bits and Cout was observed due to carry-chain loading, which was mitigated through careful sizing.  

This experiment reinforced concepts of **hierarchical design, timing analysis, transistor sizing,** and **power-delay trade-offs** in CMOS arithmetic circuits.



