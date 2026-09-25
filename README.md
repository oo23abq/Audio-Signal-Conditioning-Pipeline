# Precision, Analogue Signal Conditioning Board for ADC Aquisition

**Overview**
* This project implements a complete analogue front-end (AFE) for conditioning audio/sensor signals before digitisation by an AD4695 high‑resolution ADC.
* Simulated and verified in LTspice & designed in KICAD.

The system includes:

* A preamp stage
* A high‑pass filter (HPF)
* A low‑pass filter (LPF)
* A precision VMID bias network
* A fully‑differential ADC driver
* A 3.3 V LDO rail
* ±12 V analog supply rails
* Full hierarchical KiCad schematic design
* LTspice simulation of all analogue blocks

In total, the design uses 36 caps, 33 resistors, 2 silicon diodes, 3 connectors, 15 test points and a selection of 10 ICs. 
*  Total = 99 components  
* The six opamps used were all ADA4084‑2 dual models, chosen for their low noise, high BW, and excellent linearity.

This repository documents the entire engineering workflow, including schematic design, simulation, PCB layout, testing, and future improvements.

System Architecture
  *The signal chain is structured as follows -->
  
1) Preamp Stage
    * Differential microphone/sensor input
    * RF/ESD protection
    * Gain + impedance matching

2) High‑Pass Filter (HPF)
    * Removes DC offset
    * Sets lower cutoff (~15–20 Hz depending on configuration)
    * Biased at VMID

3) Low‑Pass Filter (LPF)
    * Sallen‑Key topology
    * Sets upper cutoff (~15–20 kHz)
    * Unity gain
    * Biased at VMID

4) ADC Driver
    * Fully differential
    * Sets ADC common‑mode
    * Drives AD4695 input stage

5) ADC Interface
    * Reference (4.096 V)
    * LDO (3.3 V)
    * Digital interface pins

6) Power Rails
    * ±12 V analogue rails
    * 3.3 V LDO
    * VMID bias generator
    * Reference buffer

Key Features
  * Hierarchical KiCad design with clean sheet‑to‑sheet signal flow
  * Zero ERC errors (verified)
  * Proper VMID/GND separation
  * Full LTspice simulation of each stage
  * Modular archiecture for easy reuse

Fabricated by JLCPCB.


```markdown
## Repository Structure

```text
├── docs/                                       # General Documentation  
│   └── report/                                 
│       └── sig_conditioning_board_report.docx  # Lab Test Report 
├── gerbers/                                    # Manufacturing Files
│   └── audioafegerbers.zip                     # Production Gerber and drill archives
├── images/                                     # 3D Renders 
│   └── pcb/                                    
│       └── 3dpcb.png                           # Assembled Board 
├── kicad/                                      # Complete KiCad hardware project
│   ├── schematics/                             # Hierarchical Schematics
│   │   ├── signal_conditioning_top.kicad_sch   # Top Level 
│   │   ├── conditioning_input.kicad_sch        # Input Stage
│   │   ├── conditioning_preamp.kicad_sch       # Preamplifier 
│   │   ├── conditioning_highpass.kicad_sch     # High-Pass Filter
│   │   ├── conditioning_lowpass.kicad_sch      # Low-Pass Filter
│   │   ├── conditioning_driver.kicad_sch       # ADC Driver / Buffer
│   │   ├── conditioning_adc.kicad_sch          # ADC Interface
│   │   ├── conditioning_power.kicad_sch        # Power / Rails 
│   │   └── conditioning_testpoints.kicad_sch   # Test Points
│   ├── signal_conditioning_top.kicad_pcb       # PCB Board File 
│   └── signal_conditioning_bom.csv             # Bill of Materials
├── ltspice/                                    # Analogue Simulation 
│   └── waveform.png                            # Transient / Hz Response Plots 
├── LICENSE                                     # MIT License File
└── README.md                                   # Project Guidance / Info 
