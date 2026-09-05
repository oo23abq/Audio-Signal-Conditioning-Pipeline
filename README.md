# Precision, Analogue Signal Conditioning Board for ADC Aquisition
A completely analogue, front‑end signal chain (HPF → LPF → ADC driver) for high‑resolution AD4695 acquisition with VMID biasing
Simulated and verified in LTspice & designed in KICAD.

**Overview**
This project implements a complete analogue front-end (AFE) for conditioning audio/sensor signals before digitisation by an AD4695 high‑resolution ADC. 

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

The design uses six ADA4084‑2 dual op‑amps, chosen for their low noise, high bandwidth, and excellent linearity.

This repository documents the entire engineering workflow, including schematic design, simulation, PCB layout, testing, and future improvements.

System Architecture
The signal chain is structured as follows:

Preamp Stage
Differential microphone/sensor input
RF/ESD protection
Gain + impedance matching

High‑Pass Filter (HPF)
* Removes DC offset
* Sets lower cutoff (~15–20 Hz depending on configuration)
* Biased at VMID

Low‑Pass Filter (LPF)
* Sallen‑Key topology
* Sets upper cutoff (~15–20 kHz)
* Unity gain
* Biased at VMID

ADC Driver

* Fully differential
* Sets ADC common‑mode
* Drives AD4695 input stage

ADC Interface
* Reference (4.096 V)
* LDO (3.3 V)
* Digital interface pins

Power Rails
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

Designed for PCB fabrication (JLCPCB)

Documented version control workflow
