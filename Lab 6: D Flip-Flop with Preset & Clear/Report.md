# Lab 6 – D Flip-Flop with Asynchronous Preset & Clear



## 1. Objective
The objective of this lab is to design and simulate a **positive-edge-triggered D Flip-Flop** with **asynchronous Preset (PRE)** and **Clear (CLR)** using **Cadence Virtuoso (FreePDK45 – 45 nm CMOS)**.  
The design uses previously created **NAND3** and **Inverter** cells to construct the flip-flop and verify:
- Correct data capture on the rising edge of the clock.  
- Proper asynchronous operation of Preset and Clear inputs.  
- Timing balance through propagation-delay and power analysis.  



## 2. Procedure
1. Designed transistor-level schematics for **NAND3** and **Inverter** gates using PMOS and NMOS transistors.  
2. Set transistor dimensions to **L = 50 nm**, with initial widths of **PMOS = 300 nm** and **NMOS = 100 nm**.  
3. Constructed the **DFFP_PC** schematic using these standard cells.  
4. Added input/output pins (**D**, **CLK**, **PRE**, **CLR**, **Q**, **Q̅**) and created a testbench.  
5. Applied transient input pulses for D, CLK, PRE, and CLR using the ADE Explorer environment.  
6. Measured **tpHL**, **tpLH**, and **average propagation delays** for multiple transistor width combinations.  
7. Adjusted PMOS/NMOS sizes to achieve **tpHL ≈ tpLH** for delay symmetry.  
8. Recorded average power for each case and compared performance.  

All figures (schematics, symbols, and waveforms) are stored externally in the repository’s *images* folder.



## 3. Simulation Results

### Case 1 – PMOS = 300 nm, NMOS = 100 nm
| Parameter | Value |
|:--|--:|
| tpHL | 44.90 ps |
| tpLH | 50.75 ps |
| tpd(avg) | 47.83 ps |
| Average Power | 12.21 µW |

**Observation:** The circuit operates correctly with stable output and near-balanced timing. The slightly larger tpLH value is due to the higher PMOS resistance during charging.



### Case 2 – PMOS = 150 nm, NMOS = 100 nm
| Parameter | Value |
|:--|--:|
| tpHL | 37.48 ps |
| tpLH | 40.48 ps |
| tpd(avg) | 38.98 ps |
| Average Power | 8.48 µW |

**Observation:** Reducing the PMOS width improves power efficiency while maintaining correct functionality and acceptable timing.

---

### Case 3 – Optimized Widths (tpHL ≈ tpLH)
| Gate | PMOS (nm) | NMOS (nm) | tpHL (ps) | tpLH (ps) | Avg Delay (ps) | Power (µW) |
|:--|:--:|:--:|:--:|:--:|:--:|:--:|
| Inverter | 200 | 130 | 32.16 | 32.85 | 32.51 | 8.39 |
| NAND3 | 90 | 150 | – | – | – | – |

**Observation:** Optimized transistor widths produced nearly equal tpHL and tpLH values with reduced average delay and stable power.  



## 4. Functional Verification
| PRE | CLR | D | CLK ↑ | Q (Output) | Description |
|:--:|:--:|:--:|:--:|:--:|:--|
| 0 | 0 | D | ↑ | D | Normal operation (Q follows D) |
| 1 | 0 | – | – | 1 | Asynchronous Preset sets Q = 1 |
| 0 | 1 | – | – | 0 | Asynchronous Clear resets Q = 0 |
| 1 | 1 | – | – | Invalid | Both asserted – undefined state |

**Observation:** The waveforms confirm that Q follows D at the rising edge of CLK when Preset and Clear are inactive. When either asynchronous input is active, it overrides normal clocked operation.


## 5. Result Summary
| Case | PMOS (nm) | NMOS (nm) | Avg Delay (ps) | Power (µW) | Remarks |
|:--:|:--:|:--:|:--:|:--:|:--|
| 1 | 300 | 100 | 47.83 | 12.21 | Baseline sizing – correct operation |
| 2 | 150 | 100 | 38.98 | 8.48 | Power-optimized – minor delay change |
| 3 | 200 / 90 | 130 / 150 | 32.51 | 8.39 | Optimized tpHL ≈ tpLH – best performance |



## 6. Conclusion
The **D Flip-Flop with asynchronous Preset and Clear** was successfully designed and verified in **Cadence Virtuoso** using **FreePDK45 (45 nm CMOS)** technology.  
The optimized configuration achieved:
- Equalized rising and falling delays (≈ 32.5 ps).  
- Stable logic operation with asynchronous inputs.  
- Lower power consumption (≈ 8.4 µW).  

This demonstrates the importance of transistor sizing in achieving timing symmetry, efficient switching, and balanced power-delay performance in CMOS sequential circuits.



