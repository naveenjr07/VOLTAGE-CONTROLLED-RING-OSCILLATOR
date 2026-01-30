# Layout Design – CMOS Voltage-Controlled Ring Oscillator (180 nm)

## Objective
The objective of the layout phase is to **implement the verified CMOS VCO schematic as a full-custom physical layout** using **Cadence Virtuoso**, targeting a **180 nm CMOS technology node**.  
The layout is designed to preserve functional correctness, ensure manufacturability, and enable accurate post-layout verification.

---

## Tools and Technology
- **EDA Tool**: Cadence Virtuoso Layout Suite  
- **Technology Node**: 180 nm CMOS PDK  
- **Design Style**: Full-custom, flat layout  
- **Verification Tools**: Cadence Assura / PVS (DRC, LVS, PEX)

---

## Layout Methodology
A **flat layout approach** is adopted, where all functional blocks are implemented within a **single top-level layout cell**.  
The following blocks are physically integrated in one module:
- VCO Core
- Schmitt Trigger
- Output Buffer

This approach simplifies routing, reduces hierarchy-related overhead, and provides better control over critical signal paths in the ring oscillator loop.

---

## Layout Implementation

### VCO Core
The VCO core consists of CMOS inverter stages forming a ring oscillator.

**Design considerations:**
- Identical transistor sizing and orientation across all stages
- Symmetric placement to minimize mismatch
- Short interconnect paths to reduce delay variation
- Proper well and substrate contacts as per 180 nm design rules

---

### Schmitt Trigger
The Schmitt trigger is placed adjacent to the VCO output to minimize routing parasitics.

**Design considerations:**
- Symmetric device placement to maintain hysteresis characteristics
- Balanced pull-up and pull-down paths
- Clean routing between VCO output and Schmitt trigger input

---

### Output Buffer
The output buffer is designed to isolate the oscillator core from external loading.

**Design considerations:**
- Increased device widths for sufficient drive strength
- Robust power and ground connections
- Physical separation from the VCO core to reduce coupling

---

## Top-Level Layout Integration
All blocks are integrated within a single layout cell, forming the complete VCO system.

**Integration considerations:**
- Continuous and wide VDD/VSS rails across the layout
- Minimal routing length in the oscillator feedback loop
- Consistent metal layer usage for critical signals
- Multiple vias used to reduce resistance and improve reliability

<img width="1739" height="792" alt="VCO_LAYOUT" src="https://github.com/user-attachments/assets/50e5fd4c-ff3a-4010-bced-cf239325ee4f" />


---

## Power, Ground, and Substrate Connections
- Dedicated VDD and VSS rails implemented using upper metal layers
- Regular placement of well taps and substrate contacts
- All transistor bodies correctly tied to their respective wells
- Compliance with 180 nm PDK latch-up and spacing rules

---
## Area and Density

### Layout Area
- Total active area: 244.737 µm²

### Density
- Density : 0.120958
- Device density is consistent with 180 nm design guidelines
- Layout avoids excessive congestion and maintains sufficient routing margin

  <img width="901" height="737" alt="Screenshot from 2026-01-27 11-48-13" src="https://github.com/user-attachments/assets/21bbb530-ab97-4609-ab47-022234249947" />

---

## Layout Readiness
At the completion of the layout stage:
- All devices are placed and routed within a single module
- Layout is compliant with 180 nm design rules
- Design is ready for **DRC, LVS, and parasitic extraction**

---

## Next Steps
The completed layout proceeds to:
- **Design Rule Check (DRC)**
- **Layout vs Schematic (LVS)**
- **Parasitic Extraction (PEX)**  
followed by post-layout simulation and GDSII generation.

