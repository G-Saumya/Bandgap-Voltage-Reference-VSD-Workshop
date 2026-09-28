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
