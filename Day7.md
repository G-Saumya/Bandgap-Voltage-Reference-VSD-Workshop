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

<img width="1842" height="902" alt="BGR response" src="https://github.com/user-attachments/assets/3424c1cb-db30-4998-abb8-dad36e10298c" />

We designed for V<sub>ref</sub> = 1.2 V, but the highest value of V<sub>ref</sub> in the response is **1.235 V**. The curve has the expected umbrella shape, as discussed in the theory. The peak-to-peak variation of V<sub>ref</sub> is **3.3 mV**.

### Verifying the Circuit

#### 1. Equal Voltages at the VCVS Inputs

The two inputs of the VCVS should be at the same voltage. Therefore, the simulated values of `v(qp1)` and `v(ra1)` should be approximately equal.

$$
\boxed{v(qp1)\approx v(ra1)}
$$

<img width="1846" height="880" alt="v(qp1) and v(ra1)" src="https://github.com/user-attachments/assets/05c27ed6-c639-4b7a-9166-e1f72af4f7f1" />

Both voltages stay at the same level across the whole temperature sweep.

#### 2. Equal Currents in the Two Branches

The currents in the branches `Vid1` and `Vid2` should be the same.

<img width="871" height="453" alt="image" src="https://github.com/user-attachments/assets/76edc118-eae2-42ed-b754-80285e2a8acd" />


#### 3. CTAT and PTAT Voltages Cancel

The CTAT voltage is the V<sub>BE</sub> of Q3.

<img width="1842" height="891" alt="VBE of Q3" src="https://github.com/user-attachments/assets/4c6e5b04-73c1-4eca-aa3c-f4ddb16af088" />

<img width="550" height="125" alt="VBE slope" src="https://github.com/user-attachments/assets/ed1e7baa-39b6-4d37-a96c-f0f3c015fb70" />

The slope is **-1.656 mV/K**.

The PTAT voltage is V<sub>ref</sub> - V<sub>BE</sub>(Q3).

<img width="1837" height="902" alt="PTAT voltage" src="https://github.com/user-attachments/assets/e3996877-a592-40bc-86d8-c124777b67a1" />

<img width="552" height="97" alt="PTAT slope" src="https://github.com/user-attachments/assets/2a7daed1-7d77-41dc-8146-aa8ab47c69d6" />

The slope is **+1.648 mV/K**.

The two slopes are nearly equal in magnitude but opposite in sign, causing the CTAT and PTAT temperature dependencies to largely cancel each other. The resulting $V_{ref}$ curve is shown below.

<img width="1917" height="905" alt="Vref curve" src="https://github.com/user-attachments/assets/dd12cc8c-1c72-44b0-899e-4688f9813677" />

#### 4. Scaling of the PTAT Voltage in the Reference Branch

The PTAT voltage in the reference branch is

$$
V_{ref}-V_{BE3}=V_T\ln(8)\times\frac{R_2}{R_1}
$$

while across R1 the PTAT voltage is

$$
V(ra1)-V_{BE2}=V_T\ln(8)
$$

In our circuit R1 = 5 kΩ and R2 = 45 kΩ, so the PTAT slope in the reference branch should be about 9 times the slope across R1.

**Slope of the PTAT voltage in the reference branch:**

<img width="547" height="90" alt="Reference branch PTAT slope" src="https://github.com/user-attachments/assets/b47d36ce-1c47-4f40-a4e3-ad537144baf1" />

$$
\frac{dy}{dx}=0.00160484\ V/K
$$

Therefore,

$$
\text{Slope}=1.605\ mV/K
$$

**Slope of the PTAT voltage across R1:**

<img width="558" height="118" alt="R1 PTAT slope" src="https://github.com/user-attachments/assets/070dbf3d-9889-4285-8a64-39c85a442269" />

$$
\frac{dy}{dx}=0.0001877\ V/K
$$

Therefore,

$$
\text{Slope}=0.1877\ mV/K
$$

**Scaling factor:**

$$
\alpha=\frac{1.605}{0.1877}
$$

$$
\boxed{\alpha\approx8.55}
$$

This is roughly 9, which agrees well with the expected value from $R_2=\alpha R_1$.
