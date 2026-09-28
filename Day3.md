# Day 3: PTAT Voltage Generation

## Concepts Covered

1. PTAT voltage generation circuit
2. Principle
3. Design of the resistor R1

## PTAT Voltage Generation

<img width="952" height="540" alt="image" src="https://github.com/user-attachments/assets/bed664e8-624a-4213-968e-b299cd2c972d" />

### PTAT Voltage Generation Using Two Diode-Connected BJTs

A **PTAT (Proportional To Absolute Temperature) voltage** can be obtained by using two diode-connected BJTs, **Q1 and Q2**, whose emitter areas are in the ratio **1:N**. Thus, **Q2 is N times larger than Q1**.

A current mirror, op-amp, or VCVS is used to make the voltages at **nodes A and B equal to the same voltage \(V\)**. As a result, both branches carry the same current \(I\).

For **Q1**, the entire current \(I\) flows through it. Therefore,

$$
V = V_T\ln\left(\frac{I}{I_S}\right)
$$

Since **Q2 has an emitter area N times larger**, its current density is \(I/N\). Hence, the voltage across Q2 is

$$
V_1 = V_T\ln\left(\frac{I/N}{I_S}\right)
$$

Now, taking the difference between the two voltages,

$$
V-V_1
=V_T\ln\left(\frac{I}{I_S}\right)
-V_T\ln\left(\frac{I/N}{I_S}\right)
$$

The \(I_S\) terms cancel, giving

$$
\boxed{V-V_1=V_T\ln(N)}
$$

This voltage difference appears across **\(R_1\)**. Since

$$
V_T=\frac{kT}{q}
$$

and \(\ln(N)\) is a constant, the voltage across \(R_1\) is directly proportional to absolute temperature. Therefore, it is a **PTAT voltage**.

### Temperature dependence

The thermal voltage is

$$
V_T=\frac{kT}{q}
$$

Therefore,

$$
\frac{dV_T}{dT}=\frac{k}{q}\approx86\ \mu V/K
$$

### Nature of the different voltages

* **\(V\)** — CTAT in nature, with a **smaller negative temperature slope**.
* **\(V_1\)** — CTAT in nature, with a **larger negative temperature slope**.
* **\(V-V_1\)** — PTAT in nature because it is proportional to \(V_T\ln(N)\).

## Design of R1 Resistance

<img width="940" height="385" alt="image" src="https://github.com/user-attachments/assets/59cac808-e5de-4532-a83e-9ab3f6a909c9" />

### Choosing the Value of \(R_1\)

The value of **\(R_1\)** is mainly determined by the **power consumption** allowed in the circuit and the available **silicon area**.

Since the voltage across \(R_1\) is the PTAT voltage,

$$
V_{R1}=V_T\ln(N)
$$

and the current through it is \(I\), the required resistance is

$$
\boxed{R_1=\frac{V_T\ln(N)}{I}}
$$

From this relationship:

* **If the circuit current \(I\) increases**, \(R_1\) becomes smaller. A smaller resistor generally requires **less silicon area**.
* **If the circuit current \(I\) decreases**, \(R_1\) needs to be larger, which generally means **more silicon area**.
* The value of \(R_1\) also changes with **\(N\)**, the area ratio between Q1 and Q2. Increasing \(N\) increases \(\ln(N)\), and therefore increases the required resistance.

For example, when

$$
I=10\,\mu A,\qquad N=8
$$

using $V_T\approx 26\,mV$ at room temperature, 

$$
R_1=\frac{26mV\times\ln(8)}{10\mu A}
\approx5.4\,k\Omega
$$

## Lab 5 Component

### Circuit

The circuit used for the simulation is shown below.

<img width="650" alt="PTAT circuit used in simulation" src="https://github.com/user-attachments/assets/c5589297-6ebd-4d43-a7eb-c2651eaad15d" />

### SPICE code

Below is the SPICE code for the PTAT voltage generation circuit.

<img width="800" alt="SPICE code for PTAT circuit" src="https://github.com/user-attachments/assets/f9612e67-b424-4c4d-9fb7-a7ccb654183a" />

### Generating the PTAT voltage

The idea of PTAT generation is to take the difference between two unequal CTAT voltages. The voltage vs temperature curve below shows the two CTAT voltages: V(qp2), the emitter voltage of Q2, and V(ra1), the node at the top of the 5.15 kΩ resistor R1.

<img width="800" alt="V(qp2) and V(ra1) vs temperature" src="https://github.com/user-attachments/assets/4fdcba37-4f90-481c-95fa-969d597fe26b" />

From the theoretical calculation, V(ra1) - V(qp2) = Vt ln(8). This difference is plotted below.

<img width="800" alt="V(ra1) - V(qp2) vs temperature" src="https://github.com/user-attachments/assets/5cbca6e4-40eb-41d1-ba2e-c82718330210" />

The plot has a positive slope, so the voltage has a positive temperature coefficient.

### Branch currents

Our design choice was for the same current to flow through Q1 and Q2. The current is given by

I = Vt ln(8) / R1

For T = 300 K and R1 = 5.15 kΩ, Vt = 0.026 V, so I ≈ 10.5 µA. This is the theoretically calculated value.

Below is the current plot from the simulation. The currents in both branches are equal.

<img width="800" alt="Branch currents vs temperature" src="https://github.com/user-attachments/assets/a30f9277-d542-4df4-b9d3-a22fccdad51b" />

<img width="800" alt="Branch current at 27 degrees C" src="https://github.com/user-attachments/assets/33805e36-f81e-4f2e-bcac-1a5923f69098" />

<img width="299" alt="Current value at 27 degrees C" src="https://github.com/user-attachments/assets/b7c47999-a752-4e29-b0b7-7e6b1e867d9c" />

At 27 °C (300 K), the simulated current is about 10.8 µA, which is close to the theoretically calculated value.
