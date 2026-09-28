# Day 2: CTAT Voltage Generation Circuit

## Concepts Covered

1. CTAT voltage generation circuit: principles
2. Design equations
3. SPICE simulation for the labs

---

## 1. CTAT Voltage Generation Circuits

A CTAT voltage can be generated using any electronic device that shows a negative temperature coefficient. Two common methods are a normal p-n junction diode and a diode-connected BJT (base shorted to collector), both of which produce a forward voltage that falls as temperature rises.

Diode-connected BJTs are generally preferred because they are easy to fabricate in standard CMOS processes (using the parasitic vertical PNP formed by the p-substrate, n-well, and p+ diffusion) and their base-emitter voltage is well characterized and predictable over temperature.

<img width="920" height="360" alt="CTAT generation circuits" src="https://github.com/user-attachments/assets/f566aea5-1c29-4435-8795-c444b9a64164" />

---

### Fig. a) Diode Fabrication Structure

<img width="625" height="357" alt="Diode fabrication structure" src="https://github.com/user-attachments/assets/0b43e362-d4d3-44b2-bbc3-650c3c8f9f90" />

In a standard CMOS process, the p-substrate is tied to ground, so a conventional diode with a freely accessible anode and cathode cannot be realized here.

### Fig. b) BJT

<img width="582" height="294" alt="BJT structure" src="https://github.com/user-attachments/assets/1292179f-b2ed-41e8-8ecd-3deb126e5fc3" />

### Fig. c) BJT as Diode

<img width="957" height="402" alt="BJT as diode" src="https://github.com/user-attachments/assets/45010420-aa2f-4277-acd1-4f5ff97b87e2" />

- Structure (b) is avoided because its P-substrate is permanently grounded, whereas (c) provides an isolated BJT current path suitable for generating V<sub>BE</sub> in the BGR.
- In (c), the current from emitter to collector is not affected by the current from emitter to base.

---

## 2. Negative Temperature Coefficient

<img width="950" height="512" alt="Negative temperature coefficient" src="https://github.com/user-attachments/assets/c0dd2991-b197-4be0-b969-7472905c381e" />

As seen above, the PN junction between the emitter and base provides the negative temperature coefficient.

<img width="527" height="157" alt="Temperature coefficient formula" src="https://github.com/user-attachments/assets/1715f341-93da-4225-942d-118b1d47af7e" />

For V<sub>BE</sub> = 700 mV and T = 300 K, this formula gives a temperature coefficient of around **-1.9 mV/K**.

---

## 3. Variation of the Slope with the Number of Transistors

<img width="932" height="262" alt="Slope vs number of transistors" src="https://github.com/user-attachments/assets/844e9288-5c7a-477f-a32a-5097df8f717b" />

As the number of BJTs increases, the slope becomes more and more negative. Adding more BJTs in parallel at a fixed total current lowers each BJT's current density, which reduces V<sub>BE</sub> and makes its slope with temperature more negative.

---

## 4. Variation of the Slope with Collector Current

<img width="882" height="413" alt="Slope vs collector current" src="https://github.com/user-attachments/assets/0dac4416-5a73-45b1-9d37-726423230cef" />

As seen above, as the collector current is increased, the current density increases and the slope becomes less and less negative.

---

## Lab: CTAT Voltage Generation

### Circuit

The circuit used for the simulation is shown below.

<img width="207" height="290" alt="Lab circuit" src="https://github.com/user-attachments/assets/bce1faf1-58bf-484b-88a7-407b616c2f47" />

### SPICE Code

Below is the SPICE code for the CTAT voltage generation circuit.

<img width="955" height="530" alt="SPICE code" src="https://github.com/user-attachments/assets/5aea152a-a978-4521-85e7-1118430dcc13" />

### V<sub>BE</sub> vs Temperature

The voltage vs temperature curve is shown below.

<img width="1591" height="856" alt="VBE vs temperature" src="https://github.com/user-attachments/assets/3ce17f31-acda-4189-903d-3d999b38eae8" />

<img width="767" height="471" alt="VBE vs temperature slope" src="https://github.com/user-attachments/assets/044f6d5e-ff08-4287-9b4e-c8bb71a319cd" />

- Slope measured from simulation: **-1.723 mV/K**
- Slope from theoretical calculation: **-1.88 mV/K**

### Effect of the Number of BJTs

The voltage vs temperature curve for m = 8 (BJT multiplier) is shown below.

<img width="697" height="538" alt="VBE vs temperature, m = 8" src="https://github.com/user-attachments/assets/9053988d-285e-463c-810c-d019f81edd30" />

The slope measured from simulation is **-1.97 mV/K**, which is more negative than for a single BJT, in line with the discussion above.

<img width="538" height="90" alt="Slope for m = 8" src="https://github.com/user-attachments/assets/f12cfe41-faa7-45f9-a11e-47352a003be1" />

### Effect of the Collector Current

The voltage vs temperature curve for a varying current is shown below. The current was varied from 1.25 µA to 10 µA.

<img width="1845" height="877" alt="VBE vs temperature for varying current" src="https://github.com/user-attachments/assets/5e8ada74-1772-494c-837e-1a8d1d36a910" />

- Slope at 1.25 µA: **-1.929 mV/K**
- Slope at 10 µA: **-1.757 mV/K**

<img width="665" height="335" alt="Slope for varying current" src="https://github.com/user-attachments/assets/2cf45743-54e4-4b2c-a60b-fa15ca53801d" />

The slope becomes less negative as the current increases, in line with the discussion above.
