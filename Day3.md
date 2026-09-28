Day 3: PTAT Voltage Generation
Concepts covered: 
1) PTAT voltage generation circuit.
2) principle.
3) Design of the resistor R1.

PTAT Voltage Generation
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
\frac{dV_T}{dT}=\frac{k}{q}\approx86\\mu V/K
$$

### Nature of the different voltages

* **\(V\)** — CTAT in nature, with a **smaller negative temperature slope**.
* **\(V_1\)** — CTAT in nature, with a **larger negative temperature slope**.
* **\(V-V_1\)** — PTAT in nature because it is proportional to \(V_T\ln(N)\).
