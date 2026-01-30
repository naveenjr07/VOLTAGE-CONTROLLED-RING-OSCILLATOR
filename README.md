# CMOS Voltage-Controlled Ring Oscillator (VCO)

## Overview
This project demonstrates the **complete custom IC design flow of a CMOS Voltage-Controlled Ring Oscillator (VCO)** using **Cadence Virtuoso** — from **schematic design** to **GDSII generation**.

The VCO is implemented using a **CMOS inverter-based ring oscillator**, where the oscillation frequency is controlled by an external analog control voltage.  
The repository is structured to closely follow **industry-standard analog/mixed-signal design methodology**, making it easy to understand and reuse.

---

## Theory (Brief)
A ring oscillator consists of an **odd number of inverting stages connected in a closed loop**. Oscillation occurs due to the cumulative propagation delay around the loop.

**Oscillation Frequency:**

f_osc = 1 / (2 · N · t_d)

Where:
- **N** → Number of inverter stages  
- **t_d** → Propagation delay per stage  

In a **Voltage-Controlled Ring Oscillator (VCO)**, the propagation delay (**t_d**) is modulated using a control voltage (**Vctrl**), enabling frequency tuning.  
This principle is widely used in **PLLs, clock generators, and SerDes systems**.

---

## Design Flow (Cadence Virtuoso)

### 1. Schematic Design
- CMOS inverter-based ring oscillator
- Odd number of stages to ensure oscillation
- Control voltage used to vary inverter delay


<img width="1730" height="880" alt="VCO" src="https://github.com/user-attachments/assets/e48a1628-02d5-4f5f-a9e4-db26d0f10db7" />


---

### 2. Testbench Setup
- Dedicated testbench for VCO characterization
- Control voltage sweep (Vctrl)
- Proper supply, ground, and load conditions


<img width="712" height="554" alt="VCO_TB-schematic" src="https://github.com/user-attachments/assets/d206e98f-9a77-47ae-b0db-a8cb1848c9f4" />


---

### 3. Pre-Layout Simulation
- Transient analysis to verify oscillation
- Frequency vs control voltage (V–f characteristic)
- Duty cycle and waveform quality evaluation


<img width="1916" height="857" alt="Screenshot from 2026-01-27 11-43-47" src="https://github.com/user-attachments/assets/a06a8732-ef31-4177-a5d7-81bb7e7ddf27" />


<img width="1920" height="979" alt="Screenshot from 2026-01-30 15-51-26" src="https://github.com/user-attachments/assets/542528d5-fa1f-4ba8-9b88-48269d93cebf" />


---

### 4. Layout Design
- Full custom CMOS layout
- Symmetric placement of inverter stages
- Proper routing and power distribution


<img width="1920" height="1080" alt="Screenshot from 2026-01-24 17-35-24" src="https://github.com/user-attachments/assets/44bc6723-00f4-404a-91cd-3acca04f894c" />


---

### 5. Physical Verification
- **DRC** – Design Rule Check
<img width="635" height="593" alt="Screenshot from 2026-01-30 16-56-31" src="https://github.com/user-attachments/assets/80da564e-d056-4d14-9cc8-67f04dddbdeb" />

<img width="198" height="117" alt="Screenshot from 2026-01-28 16-06-42" src="https://github.com/user-attachments/assets/6d7ca7c8-459b-4825-816e-c8e8e4371763" />

- **LVS** – Layout vs Schematic
<img width="635" height="684" alt="Screenshot from 2026-01-30 16-57-02" src="https://github.com/user-attachments/assets/3cc0072b-8be1-4b38-bffc-a5b5d370e5c0" />

<img width="409" height="501" alt="Screenshot from 2026-01-30 16-57-44" src="https://github.com/user-attachments/assets/c498bc89-8483-485f-9d20-6b6c33944563" />

- **PEX** – Parasitic Extraction  

<img width="1739" height="852" alt="av-extr" src="https://github.com/user-attachments/assets/7493721c-41ea-4576-bc83-76f4634f348f" />

---

### 6. Post-Layout Simulation
- Simulations using extracted netlist
- Frequency shift due to parasitics analyzed
- Comparison with pre-layout results


<img width="1920" height="1080" alt="Screenshot from 2026-01-27 11-39-33" src="https://github.com/user-attachments/assets/08912a0a-05bb-465f-98e0-37c489246fd8" />


---

### 7. GDSII Generation
- Final **GDS file** generated for fabrication readiness



---

### 🔧 Design Environment
- **EDA Tool:** Cadence Virtuoso
- **Design Level:** Transistor-level (CMOS)
- **Circuit Type:** Delay-line based ring oscillator
- **Technology:** CMOS (GPDK180-based)

---

## 👤 Authors
[Naveen J](https://www.linkedin.com/in/naveenjeyakumar)

[Lingeshwaran S](https://www.linkedin.com/in/lingeshwaran205)

## Under the guidance of:

[Dr.Elango S](https://www.linkedin.com/in/elango-sekar-8973b958)

---


