# Lab 4 – Transistor-Level Design of Basic CMOS Logic Gates
 
---

## Objective
Design and simulate transistor-level schematics of **NAND2, AND2, AND3, NOR2, NOR3, OR2, OR3, and XOR2** gates using **45 nm CMOS technology** in **Cadence Virtuoso**.  
Measure **tpHL**, **tpLH**, and **average power**, and resize transistors to achieve balanced rising and falling propagation delays.

---

## Procedure
1. Created the library **work_lib** and attached it to **NCSU_TechLib_FreePDK45**.  
2. Designed schematics for all basic logic gates using **PMOS_VTL** and **NMOS_VTL** devices.  
3. Connected PMOS bodies to **VDD!** and NMOS bodies to **VSS!**.  
4. Verified each schematic using *Check and Save* to ensure no connection errors.  
5. Configured **ADE Explorer** with the **Spectre** simulator for transient analysis.  
6. Applied pulse inputs to validate logic functionality for each gate.  
7. Measured **tpHL**, **tpLH**, and **average power** using waveform markers.  
8. Adjusted transistor widths (**Wp/Wn**) to minimize delay mismatch between rise and fall transitions.  
9. Generated **symbol views** for hierarchical integration in larger designs.

---

## Results

### NAND2 Gate
- Initial (Wp = Wn = 100 nm): tpHL = 7.417 ps, tpLH = 8.439 ps → Avg = 7.93 ps, Power = 3.64 × 10⁻⁷ W  
- Resized (Wp = 200 nm, Wn = 185 nm): tpHL = 6.63 ps, tpLH = 6.65 ps → Avg = 6.64 ps, Power = 6.27 × 10⁻⁷ W  

### AND2 Gate
- Initial Avg = 14.73 ps, Power = 5.89 × 10⁻⁷ W  
- Resized (Wp = 205 nm, Wn = 180 nm): Avg = 12.14 ps, Power = 9.53 × 10⁻⁷ W  

### AND3 Gate
- Initial Avg = 19.81 ps, Power = 7.64 × 10⁻⁷ W  
- Resized (Wp = 190 nm, Wn = 210 nm): Avg = 15.96 ps, Power = 1.29 × 10⁻⁶ W  

### NOR2 Gate
- Initial Avg = 5.87 ps, Power = 2.60 × 10⁻⁷ W  
- Resized (Wp = 375 nm, Wn = 100 nm): Avg = 4.54 ps, Power = 5.01 × 10⁻⁷ W  

### NOR3 Gate
- Initial Avg = 12.60 ps, Power = 4.65 × 10⁻⁷ W  
- Resized (Wp = 1.25 µm, Wn = 90 nm): Avg = 8.14 ps, Power = 2.68 × 10⁻⁶ W  

### OR2 Gate
- Initial Avg = 12.13 ps, Power = 4.72 × 10⁻⁷ W  
- Resized (Wp = 475 nm, Wn = 100 nm): Avg = 9.20 ps, Power = 8.46 × 10⁻⁷ W  

### OR3 Gate
- Initial Avg = 19.62 ps, Power = 7.04 × 10⁻⁷ W  
- Resized (Wp = 1.37 µm, Wn = 90 nm): Avg = 12.98 ps, Power = 3.27 × 10⁻⁶ W  

### XOR2 Gate
- Initial Avg = 17.34 ps, Power = 1.19 × 10⁻⁶ W  
- Resized (Wp = 300 nm, Wn = 720 nm): Avg = 16.04 ps, Power = 3.82 × 10⁻⁶ W  

---

## Before and After Resizing Summary
The following table compares the delay and power performance of each CMOS gate before and after transistor resizing.

| Gate | Wp (nm) | Wn (nm) | tpHL (ps) | tpLH (ps) | **Avg Delay (ps)** | **Power (W)** | Improvement |
|:------|:--------:|:--------:|:-----------:|:-----------:|:----------------:|:----------------:|:-------------|
| **NAND2 (Before)** | 100 | 100 | 7.417 | 8.439 | 7.93 | 3.64×10⁻⁷ | — |
| **NAND2 (After)** | 200 | 185 | 6.63 | 6.65 | 6.64 | 6.27×10⁻⁷ | Balanced tpHL/tpLH, faster delay |
| **AND2 (Before)** | 100 | 100 | 15.18 | 14.27 | 14.73 | 5.89×10⁻⁷ | — |
| **AND2 (After)** | 205 | 180 | 12.12 | 12.16 | 12.14 | 9.53×10⁻⁷ | Improved delay symmetry |
| **AND3 (Before)** | 100 | 100 | 19.73 | 19.89 | 19.81 | 7.64×10⁻⁷ | — |
| **AND3 (After)** | 190 | 210 | 15.99 | 15.94 | 15.96 | 1.29×10⁻⁶ | Reduced delay with larger Wn |
| **NOR2 (Before)** | 100 | 100 | 5.85 | 5.89 | 5.87 | 2.60×10⁻⁷ | — |
| **NOR2 (After)** | 375 | 100 | 4.56 | 4.52 | 4.54 | 5.01×10⁻⁷ | Faster transition, symmetric delay |
| **NOR3 (Before)** | 100 | 100 | 12.63 | 12.57 | 12.60 | 4.65×10⁻⁷ | — |
| **NOR3 (After)** | 1250 | 90 | 8.16 | 8.12 | 8.14 | 2.68×10⁻⁶ | 35% faster operation |
| **OR2 (Before)** | 100 | 100 | 12.13 | 12.13 | 12.13 | 4.72×10⁻⁷ | — |
| **OR2 (After)** | 475 | 100 | 9.19 | 9.20 | 9.20 | 8.46×10⁻⁷ | 24% faster, balanced delay |
| **OR3 (Before)** | 100 | 100 | 19.61 | 19.63 | 19.62 | 7.04×10⁻⁷ | — |
| **OR3 (After)** | 1370 | 90 | 12.97 | 13.00 | 12.98 | 3.27×10⁻⁶ | 34% delay reduction |
| **XOR2 (Before)** | 100 | 100 | 17.36 | 17.33 | 17.34 | 1.19×10⁻⁶ | — |
| **XOR2 (After)** | 300 | 720 | 16.02 | 16.05 | 16.04 | 3.82×10⁻⁶ | Slight delay improvement, higher drive strength |

---

## Delay and Power Summary

| Gate | Wp (nm) | Wn (nm) | tpHL (ps) | tpLH (ps) | Avg Delay (ps) | Avg Power (W) |
|:-----|:-------:|:-------:|:---------:|:---------:|:--------------:|:--------------:|
| NAND2 | 200 | 185 | 6.63 | 6.65 | 6.64 | 6.27×10⁻⁷ |
| AND2  | 205 | 180 | 12.12 | 12.16 | 12.14 | 9.53×10⁻⁷ |
| AND3  | 190 | 210 | 15.99 | 15.94 | 15.96 | 1.29×10⁻⁶ |
| NOR2  | 375 | 100 | 4.56 | 4.52 | 4.54 | 5.01×10⁻⁷ |
| NOR3  | 1250 | 90 | 8.16 | 8.12 | 8.14 | 2.68×10⁻⁶ |
| OR2   | 475 | 100 | 9.19 | 9.20 | 9.20 | 8.46×10⁻⁷ |
| OR3   | 1370 | 90 | 12.97 | 13.00 | 12.98 | 3.27×10⁻⁶ |
| XOR2  | 300 | 720 | 16.02 | 16.05 | 16.04 | 3.82×10⁻⁶ |

---

## Conclusion
All CMOS logic gates were successfully designed, simulated, and analyzed at the transistor level using **Cadence Virtuoso (45 nm CMOS)**.  
Resizing transistors—particularly widening PMOS devices—significantly reduced the difference between **tpHL** and **tpLH**.  
The optimized gates achieved nearly equal rise and fall delays with minimal power overhead, demonstrating the importance of **transistor sizing** for balanced and efficient CMOS circuit design.

