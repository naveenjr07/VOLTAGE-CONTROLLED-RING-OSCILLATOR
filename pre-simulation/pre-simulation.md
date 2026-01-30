# Pre-Layout Simulation – CMOS Voltage-Controlled Ring Oscillator

## Objective
The objective of the pre-layout simulation is to **verify functional correctness and characterize the performance of the CMOS VCO** at the schematic level, prior to physical implementation.  
All simulations are performed using the **testbench described in `testbench.md`**, without considering layout parasitics.

---

## Simulation Setup
- Simulator: Cadence Spectre
- Design level: Schematic (pre-layout)
- Testbench: Top-level VCO with Schmitt trigger and output buffer
- Control parameter: Design variable `vctrl`
- Analysis type: Transient (tran)

---

## Transient Analysis

### Purpose
- Verify oscillation startup and stability
- Observe waveform quality at the buffered output
- Confirm correct operation of Schmitt trigger and buffer stages

### Configuration
- Transient stop time selected to capture multiple oscillation cycles
- No forced initial conditions
- Output measured after buffer stage

### Result


<img width="1920" height="979" alt="Screenshot from 2026-01-30 15-51-26" src="https://github.com/user-attachments/assets/09cc2f7d-24e0-49ee-8d03-ec331a09ed69" />


The waveform shows stable and sustained oscillation after startup, indicating correct functionality of the VCO core and signal conditioning blocks.

---

## Duty Cycle Analysis

### Methodology
- Duty cycle is measured at the buffered output waveform
- High and low time durations are extracted from steady-state oscillation
- Duty cycle is calculated as:
  
  Duty Cycle (%) = (T<sub>HIGH</sub> / T<sub>PERIOD</sub>) × 100

### Observation
The output duty cycle remains close to 50% over the valid operating range, indicating balanced inverter stages and effective waveform conditioning.

<img width="648" height="779" alt="Screenshot from 2026-01-30 16-01-41" src="https://github.com/user-attachments/assets/03365f9d-2cc6-44d4-8568-ae895d379b99" />

---

## Frequency Extraction

### Methodology
- A parametric transient simulation is performed by sweeping the control voltage (`vctrl`)
- Oscillation frequency is extracted from the buffered output waveform using the calculator `freq()` function
- Frequency measurement is added as an output expression and evaluated across the sweep

---

## Observations
- Stable oscillation achieved over the valid `vctrl` range
- Frequency varies predictably with control voltage
- Output waveform is clean due to Schmitt trigger and buffer stages
- No abnormal startup or oscillation collapse observed

---

## Limitations
- Parasitic effects from interconnect and devices are not included
- Absolute frequency values may shift after layout and extraction

---

## Conclusion
Pre-layout simulations confirm that the CMOS VCO operates as intended and meets functional expectations.  
The design is therefore suitable to proceed to **layout implementation and physical verification**.

