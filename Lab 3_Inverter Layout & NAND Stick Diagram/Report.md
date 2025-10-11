# Lab 3 – CMOS Inverter Layout and 3-Input NAND Stick Diagram

## Objective
Design, implement, and verify the **layout of a CMOS inverter** using **Cadence Virtuoso (45 nm CMOS)**.  
Perform **DRC, LVS, and PEX** checks, simulate the extracted netlist in **HSPICE**, and measure propagation delays (**tpHL**, **tpLH**).  
Additionally, design the **stick diagram and schematic of a 3-input NAND (NAND3)** gate to reinforce understanding of transistor-level layout abstraction.


## Procedure

1. **Inverter Layout Design**  
   - Created a transistor-level schematic for a CMOS inverter using PMOS_VTL and NMOS_VTL devices.  
   - Designed the corresponding layout with proper **n-well**, **p-well**, **diffusion**, and **polysilicon** connections.  
   - Used **Metal-1** for interconnects and added **VDD** and **VSS rails** for power distribution.  
   - Verified design correctness through **DRC check** (no errors found).

2. **Standard Cell Alignment**  
   - Adjusted cell height to **2000 nm (y = –1000 nm to +1000 nm)**.  
   - Used **stretch** and **move** commands to align power rails and maintain standard-cell height.  
   - Confirmed layout compatibility with the standard-cell library format.

3. **Testbench Creation**  
   - Developed a **three-inverter testbench** (driver, CUT, and load).  
   - Connected symbols and verified schematic-layout correspondence using **LVS check**.  
   - Performed **PEX extraction** to generate a parasitic-aware netlist.

4. **HSPICE Simulation**  
   - Simulated the extracted netlist for transient analysis.  
   - Measured **tpHL** and **tpLH** using HSPICE waveforms and `.mt0` output files.  
   - Post-processed results in MATLAB using `tr0Reader` to visualize waveforms and confirm timing results.

5. **NAND3 Schematic and Stick Diagram**  
   - Designed and sketched the **3-input NAND schematic** at the transistor level.  
   - Created its **stick diagram** to represent layout connectivity and diffusion sharing.

  
## Results

| Case | Wp (nm) | Wn (nm) | tpHL (ps) | tpLH (ps) | Avg Delay (ps) |
|:----:|:--------:|:--------:|:----------:|:----------:|:---------------:|
| **Initial** | 100 | 100 | 7 | 10 | 8.5 |
| **Resized** | 175 | 100 | 8 | 7 | 7.5 |

### Observations
- With equal transistor widths, **tpLH > tpHL**, due to lower hole mobility in PMOS.  
- Increasing the PMOS width to **175 nm** improved the pull-up strength, balancing rise and fall delays.  
- The final design passed both **DRC** and **LVS** checks without errors.  
- **PEX-based simulation** confirmed accurate timing and power characteristics.
  

## Conclusion
The **CMOS inverter layout** was successfully designed, verified, and simulated using **Cadence Virtuoso (45 nm)**.  
Post-layout verification through **DRC**, **LVS**, and **PEX** ensured physical and functional correctness.  
By resizing the PMOS transistor, **tpHL and tpLH became nearly equal**, highlighting the importance of transistor sizing for delay optimization.  
The **NAND3 stick diagram** further strengthened understanding of diffusion sharing and series-parallel transistor arrangements used in multi-input logic gates.

