# Testbench Design – CMOS Ring VCO

## Purpose
The testbench is designed to **verify and characterize the functionality of the CMOS Voltage-Controlled Ring Oscillator (VCO)** before physical implementation.  
It provides a controlled environment to evaluate oscillation behavior, frequency tuning, and signal integrity without modifying the core design.

---

## Testbench Overview
The testbench instantiates the **top-level VCO schematic**, which includes:
- VCO core
- Schmitt trigger
- Output buffer

All external stimuli and measurement points are applied at the testbench level to maintain a **clean separation between design and verification**.

---

## Testbench Components

### 1. VCO Instance
- The complete top-level VCO is instantiated as a single block.
- Internal nodes of the VCO are not directly driven or modified in the testbench.


<img width="712" height="554" alt="VCO_TB-schematic" src="https://github.com/user-attachments/assets/3c3d24d7-5484-4c86-9d81-b871247d27e0" />


---

### 2. Power Supplies
- **VDD**: DC voltage source providing the nominal supply voltage  
- **GND**: Global ground reference  

The supply voltage is kept constant during simulations to isolate the effect of the control voltage on frequency.

---

### 3. Control Voltage Source (Vctrl)
- A DC voltage source is used to control the oscillation frequency.
- Vctrl is swept across a defined range during simulation.
- This allows extraction of the **frequency vs control voltage (V–f) characteristic**.

Typical parameters:
- Minimum Vctrl: low-frequency limit  
- Maximum Vctrl: high-frequency limit  

---

### 4. Output Load
- A light capacitive load (if applicable) is connected at the output.
- Ensures realistic output behavior without significantly loading the oscillator.

---

### 5. Measurement Nodes
- Output node connected after the buffer stage
- Used for:
  - Transient waveform observation
  - Frequency measurement
  - Duty cycle estimation

---

## Simulation Setup

### Analysis Type
- **Transient (tran) analysis** is used to observe time-domain behavior.
- Simulation time is chosen to capture multiple oscillation cycles.

### Initial Conditions
- Default simulator initial conditions are used.
- Startup behavior is observed to ensure self-sustained oscillation.

---

## Verification Objectives
The testbench is used to verify the following:

- ✔ Oscillation startup and stability  
- ✔ Correct functionality of Schmitt trigger and buffer  
- ✔ Frequency variation with control voltage  
- ✔ Output waveform quality  

---

## Notes
- The testbench does not include layout parasitics.
- All results obtained here correspond to **pre-layout performance**.
- Post-layout verification is performed using an extracted netlist in a separate stage.

---

## Outcome
The testbench successfully enables **functional verification and characterization** of the VCO prior to layout, ensuring a reliable transition to physical design.
