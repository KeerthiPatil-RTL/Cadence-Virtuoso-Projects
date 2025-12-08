# 8-bit ALU (Arithmetic Logic Unit) – Transistor-Level Design  

##  Project Overview
This project implements a **fully functional transistor-level 8-bit Arithmetic Logic Unit (ALU)** capable of performing four arithmetic and four logical operations. The ALU supports:
- **Arithmetic Operations:** Increment, Decrement, Addition, Subtraction  
- **Logical Operations:** AND, OR, Complement, Identity  

The design is based on a **bit-sliced architecture**, beginning from a single 1-bit ALU and expanding to a complete 8-bit structure using hierarchical replication.

All simulations, power analysis, and timing verification were completed in **Cadence Virtuoso**.

---

##  Features
- Transistor-level schematics for:
  - Arithmetic Extender (AE)
  - Logic Extender (LE)
  - Carry-Out Logic (CO)
  - Full Adder (Compound Gate FA)
  - 1-bit D Flip-Flop
  - 8-bit Register
- Complete 1-bit ALU (with and without registers)
- Complete 8-bit ALU (three versions):
  - Purely combinational  
  - Output-registered  
  - Fully registered (input + output registers)  
- Glitch analysis and waveform verification  
- Worst-case delay extraction  
- Power, Delay, Area (PDA) computation for design efficiency  

---

##  Floorplan Summary
The ALU uses a **regular bit-slice floorplan**:
- Each slice contains **AE → LE → FA** arranged left to right  
- Eight slices placed horizontally  
- Ripple-carry chain propagates from LSB slice to MSB slice  
- Input registers on the left, output registers on the right  
- Minimizes routing complexity and ensures timing consistency  

---

##  Design Methodology
1. Generated truth tables for all ALU operations  
2. Constructed K-maps for AE, LE, and CO  
3. Derived minimized Boolean expressions  
4. Implemented AE, LE, CO using transistor-level logic  
5. Added a compound-gate full adder  
6. Designed 1-bit DFF and 8-bit register  
7. Built the 1-bit ALU  
   - Tested without registers  
   - Tested again with registers  
8. Replicated to create an 8-bit ALU  
9. Performed glitch analysis  
10. Determined worst-case delay  
11. Measured power, area, and calculated PDA  

---

##  Power–Delay–Area (PDA) Summary

### **Unregistered 8-bit ALU**
- **Power:** 57.73 µW  
- **Delay:** 163.843 ps  
- **Area:** 8.388 µm²  
- **PDA:** 7.94 × 10⁻¹⁴  

### **Registered 8-bit ALU**
- **Power:** 113.6 µW  
- **Delay:** 243.5775 ps  
- **Area:** 9.538 µm²  
- **PDA:** 2.64 × 10⁻¹³  

The registered ALU eliminates glitches and offers stable synchronous operation at the cost of a higher PDA.

---

##  Results Summary
- All AE, LE, CO, FA, and register blocks were verified using simulation.  
- 1-bit and 8-bit ALUs produced **correct outputs** for all input combinations.  
- Glitches appeared in the combinational version but were removed by register insertion.  
- Worst-case delay was identified through ripple-carry propagation analysis.  
- PDA metrics demonstrate the tradeoff between performance stability and hardware cost.  

---

## 📂 Repository Structure (Recommended)

