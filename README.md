# Cascaded 8-Bit Synth: APC + PT2399 Delay + LM386 Amp

## Overview
A cascaded analog-to-digital synthesizer circuit. It utilizes a stepped-tone generator (dual-555 Atari Punk Console) to create a square wave, which is fed into a PT2399 digital delay memory buffer to generate pitch-warping echoes. The signal is finally routed through an LM386 audio power amplifier with a custom voltage divider for master volume control. 

## Hardware Specifications
- **ICs:** 2x NE555 (Oscillators), 1x PT2399 (Digital Delay), 1x LM386 (Audio Amplifier)
- **Controls:** 4x Potentiometers (Pitch, Pulse-Width, Delay Time, Master Volume)
- **Passive Components (Resistors):** Assorted 1kΩ (safety constraints) and 47Ω (Zobel network)
- **Passive Components (Capacitors):** Assorted 0.1µF ceramics (AC coupling), 10µF to 1000µF electrolytics (power filtering and speaker output)
- **Output:** 1x 8Ω Magnetic Speaker
- **Power & Protection:** 1x L7805 Linear Voltage Regulator (dropping 10-12V unregulated down to stable 5V logic)

## Prerequisites
To achieve the 5V power rail capable of driving the LM386 amplifier without thermal collapse, I used a multi-cell battery pack regulated to output 5V. Here is a link to the repository:
[5V Linear Breadboard Power Supply](https://github.com/mhos2006/starter-dc-makeshift-power-supply)

## Schematics
<img width="1243" height="647" alt="image" src="https://github.com/user-attachments/assets/11cd9099-686c-4596-ba82-810fea23c7fb" />


## Testing
*(Insert video demonstrating the Fire Rate, Pulse Width, Delay Time, and Volume sweeps here)*
https://github.com/user-attachments/assets/[INSERT_VIDEO_LINK_HERE]

## Construction Notes & Hardware Quirks
- **AC Coupling:** The PT2399 outputs audio on a 2.5V DC offset. A 0.1µF coupling capacitor is placed between the delay output and the LM386 input (Pin 3) to prevent DC saturation.
- **RF Oscillation Protection:** The LM386 requires a Zobel network (10Ω resistor + 0.1µF capacitor) on Pin 5 to Ground to prevent high-frequency oscillation and extreme battery drain.
- **Noise Mitigation:** LM386 Pin 2 (Inverting Input) must be anchored directly to Ground to prevent it from acting as a radio antenna for ambient electromagnetic interference. 

## Schematic and PCB Documentation
I created the schematic using KiCad software. While my schematic has been verified, I have not yet moved the components over to PCB software as I must still add accurate component footprints. PCB layout and component placement is in progress.

## Documentation
For a full breakdown of the empirical voltage measurements, signal routing, and delay buffer analysis, please see the attached technical report .docx.
