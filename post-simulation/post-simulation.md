# Post-Layout Verification and Simulation – CMOS Voltage-Controlled Ring Oscillator (180 nm)

## Objective
The objective of this stage is to **verify the physical correctness and post-layout performance** of the CMOS Voltage-Controlled Ring Oscillator (VCO) after layout implementation.  
This includes **DRC, LVS, parasitic extraction (PEX)**, and **post-layout simulations** using the extracted netlist.

---

## Tools and Technology
- **EDA Tool**: Cadence Virtuoso  
- **Physical Verification**: Assura / PVS  
- **Simulator**: Spectre  
- **Technology Node**: 180 nm CMOS  
- **Design Style**: Full-custom, flat layout  

---

## Design Rule Check (DRC)

### Purpose
- Ensure layout compliance with 180 nm process design rules
- Detect spacing, width, enclosure, and connectivity violations

### Result

<img width="635" height="593" alt="Screenshot from 2026-01-30 16-56-31" src="https://github.com/user-attachments/assets/83131ae5-4428-417d-8d57-dcade1b92086" />

<img width="198" height="117" alt="Screenshot from 2026-01-28 16-06-42" src="https://github.com/user-attachments/assets/33fb49f6-cb41-4483-b2ee-42f8b0ec1801" />

**Observation:**
- The layout passes all design rule checks
- No DRC violations are reported

This confirms that the layout is **manufacturable** under the selected technology rules.

---

## Layout vs Schematic (LVS)

### Purpose
- Verify logical equivalence between layout and schematic
- Ensure correct device count, connectivity, and hierarchy mapping

### Result

<img width="635" height="593" alt="Screenshot from 2026-01-30 16-56-31" src="https://github.com/user-attachments/assets/c18bf375-6821-4574-b6dc-a670c4315dd1" />

<img width="409" height="501" alt="Screenshot from 2026-01-30 16-57-44" src="https://github.com/user-attachments/assets/dcad7a11-fca7-4f7f-8002-e87651222750" />

**Observation:**
- LVS reports a clean match
- All devices and nets correspond correctly between schematic and layout

This confirms that the physical layout **faithfully represents the intended design**.

---

## Parasitic Extraction (PEX)

### Purpose
- Extract interconnect parasitic resistances and capacitances
- Enable accurate post-layout performance evaluation

### Extraction Details
- RC parasitics extracted using Assura / PVS
- Extracted view used for all post-layout simulations

<img width="1739" height="852" alt="av-extr" src="https://github.com/user-attachments/assets/8a81b49d-3ce7-4f99-ab99-9632da47b2dd" />


**Observation:**
- Parasitic components are successfully included
- Extracted netlist reflects realistic loading conditions

---

## Post-Layout Simulation Setup
- Netlist: Extracted (post-PEX) view
- Testbench: Same as pre-layout simulations
- Control parameter: Design variable `vctrl`
- Analysis type: Transient (tran)

---

## Transient Analysis (Post-Layout)

### Purpose
- Verify oscillation startup with parasitics included
- Confirm stable steady-state operation

### Result

<img width="1674" height="855" alt="Screenshot from 2026-01-27 11-39-37" src="https://github.com/user-attachments/assets/a52fb3fd-f8cb-4b68-95bc-5664549e6698" />

The waveform shows stable oscillation, indicating that parasitic effects do not inhibit startup or sustained operation.

---

## Duty Cycle Analysis
- Duty cycle measured at buffered output under steady-state conditions

**Observation:**
- Duty cycle remains close to 50%
- Minimal distortion introduced by layout parasitics

<img width="648" height="779" alt="Screenshot from 2026-01-30 16-01-41" src="https://github.com/user-attachments/assets/c51feb93-52de-493a-9278-67dfe3dcece8" />

---

## Power Consumption

### Methodology
- Average supply current measured from VDD
- Power computed as:

  Power = VDD × I<sub>avg</sub>

**Observation:**
- Slight increase in power consumption compared to pre-layout
- Increase attributed to parasitic loading and interconnect resistance

---

## Pre-Layout vs Post-Layout Comparison

| Parameter    | Pre-Layout | Post-Layout | Remark |
|-------------|-----------|------------|--------|
| Oscillation | Stable | Stable | No functional degradation |
| Frequency   | Higher | Reduced | Parasitic effects |
| Duty Cycle  | ~50% | ~50% | Minimal impact |
| Power       | Lower | Slightly higher | Expected |

---

## Conclusion
The CMOS VCO successfully passes **DRC and LVS**, and post-layout simulations using the **extracted netlist** confirm stable operation.  
Although parasitics introduce expected shifts in frequency and power, overall functionality and tuning behavior are preserved.

The design is therefore **verified, extraction-aware, and ready for final GDSII generation**.

