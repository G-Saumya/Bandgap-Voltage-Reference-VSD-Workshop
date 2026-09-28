# Day 7: Complete BGR Circuit

## Concepts Covered

The complete bandgap voltage reference circuit, and a summary of Days 1 to 6.

## Complete BGR Circuit

<img width="812" height="530" alt="image" src="https://github.com/user-attachments/assets/5c56a300-c371-4edd-bc08-f0b322eb343b" />

## BGR Complete Circuit: Days 1–6

The BGR consists of four main blocks:

* **SBCM:** $M_{P1}, M_{P2}, M_{N1}, M_{N2}$ — generates a supply-independent current. **(Day 4)**
* **CTAT & PTAT:** $Q_1, Q_2, R_1$ — generates the CTAT and PTAT components. **(Days 2–3)**
* **Reference Branch:** $M_{P3}, R_2, Q_3$ — combines them to generate $V_{ref}$. **(Day 5)**
* **Start-Up Circuit:** $M_{P4}, M_{P5}, M_{N3}$ — starts the circuit from the zero-current state. **(Day 6)**

### Summary

* **Day 1:** BGR generates a ~1.2 V reference by cancelling CTAT and PTAT temperature dependencies.
* **Day 2 (CTAT Voltage Generation):** The base-emitter voltage $V_{BE}$ of a diode-connected BJT has a negative temperature coefficient, making it CTAT. BJTs are commonly used because they can be integrated into CMOS processes. The $V_{BE}$ temperature slope depends on the device and current density.
* **Day 3 (PTAT Voltage Generation):** Two BJTs with an emitter-area ratio of $1:N$, carrying the same current, produce a voltage difference $\Delta V_{BE}=V_T\ln(N)$ across $R_1$. Since $V_T=\dfrac{kT}{q}$, this voltage is PTAT. The resistor is designed using $R_1=\dfrac{V_T\ln(N)}{I}$, so $R_1$ depends on the bias current and the BJT area ratio $N$.
* **Day 4:** Self-biased current mirror generates a supply-independent current; $R_S$ sets the current level.
* **Day 5:** CTAT and PTAT components are added, $V_{ref}=V_{BE3}+I_3R_2$, where $R_2$ is chosen for zero temperature coefficient.
* **Day 6:** Start-up circuit removes the zero-current state at power-up and turns OFF during normal operation.

## Putting It Together

The reference voltage is

$$
V_{ref}=V_{BE3}+\alpha V_T\ln(N)
$$

where the first term is **CTAT** and the second is **PTAT**.

For zero temperature coefficient:

$$
\alpha\ln(N)=
\frac{\left|\frac{dV_{BE3}}{dT}\right|}
{\frac{dV_T}{dT}}
$$

### Design Flow

1. Choose $I$ and $N$.
2. Calculate $R_1=\dfrac{V_T\ln(N)}{I}$.
3. Calculate $\alpha$ for zero temperature coefficient.
4. Calculate $R_2=\alpha R_1$.

**Example:** For $I=10\,\mu A$ and $N=8$:

$$
R_1\approx5.4\,k\Omega,\qquad \alpha\approx9
$$

Therefore,

$$
R_2\approx49\,k\Omega
$$

and

$$
V_{ref}\approx1.2\,V
$$

## Lab 6: BGR Simulation

### Circuit

The circuit used for the simulation is shown below.

<img width="1063" height="892" alt="BGR lab circuit" src="https://github.com/user-attachments/assets/836efa19-14d1-4857-a3f5-120fa9d5a789" />

### SPICE Code

The SPICE code spans the two images below.

<img width="1187" height="891" alt="SPICE code part 1" src="https://github.com/user-attachments/assets/0387a3a8-2d74-40fa-9f0e-d62c548e39c6" />

<img width="811" height="803" alt="SPICE code part 2" src="https://github.com/user-attachments/assets/5ab8ed2f-8ce7-4f21-91c5-72649b3c2e74" />

### BGR Response

The BGR response is shown below.

<img width="1848" height="886" alt="BGR response" src="https://github.com/user-attachments/assets/81d1451a-0f4e-4f40-a842-e70d7f1c976a" />

<img width="511" height="207" alt="Vref measurements" src="https://github.com/user-attachments/assets/c49f9e1a-fe82-4a6d-ae91-ae8f20c008ef" />

We designed for V<sub>ref</sub> = 1.2 V, but the highest value of V<sub>ref</sub> in the response is **1.23581 V**. The curve has the expected umbrella shape, as discussed in the theory. The peak-to-peak variation of V<sub>ref</sub> is **3.38 mV**.

### Verifying the Circuit

1.**Equal voltages at the VCVS inputs.** The two inputs of the VCVS should be at the same voltage, so `v(qp1)` and `v(ra1)` should be equal (see the circuit diagram).
