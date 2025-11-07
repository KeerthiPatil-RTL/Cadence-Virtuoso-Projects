# Lab 07 – 4-Bit Binary and Decimal Down Counter

##  Objective
To design, implement, and verify a **4-bit binary and decimal down counter** at the transistor level using Cadence Virtuoso.  
The goal was to demonstrate sequential circuit operation using D Flip-Flops and logic gates, validate asynchronous reset and ripple-carry output functions, and determine the **maximum operating frequency** for reliable operation.



##  Procedure
- Designed a **4-input NOR** gate specifically for this lab to complete the control logic.  
- Used verified **AND2, OR2, and NOT** gates from earlier labs to build the required combinational network.  
- Implemented the **DFFP** schematic from the previous lab as the sequential element for each bit of the counter.  
- Connected **BinDec**, **RESET**, and **CLK** as control inputs to select between binary and decimal counting modes.  
- Performed transient simulations with the following pulse stimuli:  
  - **CLK:** Period = 2 ns, Width = 1 ns  
  - **RESET:** Period = 30 ns, Width = 1 ns  
  - **BinDec:** Period = 40 ns, Width = 20 ns  
- Gradually increased the clock frequency to identify the **highest stable frequency** maintaining correct outputs.



##  Simulation Results

| Case | Clock Period (ns) | Clock Frequency (GHz) | Observation | Functionality |
|:----:|:------------------:|:---------------------:|:-------------|:--------------|
| Given Stimuli | 2 | 0.5 (500 MHz) | Both modes operated correctly |  Fully functional |
| Case 1 | 1 | 1 | Stable operation in both modes |  Functional |
| Case 2 | 0.5 | 2 | Minor glitches observed, correct outputs |  Highest stable frequency |
| Case 3 | 0.25 | 4 | Multiple glitches, incorrect outputs |  Failed operation |



##  Design Optimization and Analysis
In combinational circuits, PMOS and NMOS widths are adjusted to balance tpLH and tpHL for symmetrical transitions.  
In **sequential circuits** such as counters, transistor widths are optimized to achieve reliable operation at higher clock frequencies.  
Increasing NMOS width strengthens the pull-down path and improves switching speed, while increasing PMOS width enhances pull-up drive and reduces rise time.  
Proper transistor sizing improves **setup and hold-time margins**, enabling **glitch-free** operation and stable performance at high frequencies.



## Conclusion
The 4-bit binary and decimal down counter was successfully designed and simulated using transistor-level schematics in Cadence Virtuoso.  
The circuit operated correctly up to **2 GHz**, beyond which glitches and timing issues appeared.  
This experiment demonstrates the influence of clock frequency on sequential-circuit reliability and highlights the importance of transistor sizing and timing optimization in high-speed digital design.



