## Schematic Design

The design is implemented using a **hierarchical approach**, consisting of three main functional blocks:

### VCO Core
The VCO core is a CMOS inverter-based ring oscillator whose frequency is controlled using an analog control voltage (Vctrl).


<img width="1731" height="880" alt="VCO-schematic" src="https://github.com/user-attachments/assets/9a429595-1010-49ce-8e01-b2af459c5029" />


### Schmitt Trigger
A Schmitt trigger is used to convert the raw oscillation waveform into a clean digital signal by introducing hysteresis and improving noise immunity.


<img width="711" height="554" alt="SCHMITT" src="https://github.com/user-attachments/assets/bc267f86-22e0-458a-87eb-33b42ee39e83" />


### Output Buffer
The output buffer isolates the oscillator from the load and provides sufficient drive strength without affecting the oscillation frequency.


<img width="1732" height="880" alt="BUFF" src="https://github.com/user-attachments/assets/6c1f02ee-0750-485a-99bc-0d3914663dd4" />


### Top-Level Integration
All blocks are integrated at the top level, forming a modular and scalable VCO system suitable for mixed-signal applications.

<img width="1730" height="880" alt="VCO" src="https://github.com/user-attachments/assets/71f518cf-39f5-4f91-aef3-9b30aaac56a9" />

