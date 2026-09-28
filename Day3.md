# Day 3: PTAT Voltage Generation

## Concepts Covered

1. PTAT voltage generation circuit
2. Principle of PTAT voltage generation
3. Design of resistor \(R_1\)

---

## 1. PTAT Voltage Generation

**PTAT** stands for **Proportional To Absolute Temperature**.

A PTAT voltage can be generated using two diode-connected BJTs, \(Q_1\) and \(Q_2\), having an emitter area ratio of **1:N**. Therefore, \(Q_2\) has an emitter area \(N\) times larger than \(Q_1\).

![PTAT Voltage Generation Circuit](https://github.com/user-attachments/assets/bed664e8-624a-4213-968e-b299cd2c972d)

### Principle of Operation

A current mirror, op-amp, or VCVS forces nodes **A and B** to the same voltage \(V\). Consequently, the same current \(I\) flows through both branches.

For \(Q_1\), the complete current \(I\) flows through the transistor:

\[
V = V_T \ln\left(\frac{I}{I_S}\right)
\]

where:

- \(V_T\) = thermal voltage
- \(I\) = collector current
- \(I_S\) = saturation current

Since \(Q_2\) has an emitter area \(N\) times larger than \(Q_1\), its current density is reduced by a factor of \(N\). Therefore,

\[
V_1 = V_T \ln\left(\frac{I/N}{I_S}\right)
\]

Taking the difference between the two voltages:

\[
V - V_1 =
V_T\ln\left(\frac{I}{I_S}\right)
-
V_T\ln\left(\frac{I/N}{I_S}\right)
\]

The \(I_S\) terms cancel:

\[
\boxed{V-V_1=V_T\ln(N)}
\]

This voltage difference appears across \(R_1\).

Since

\[
V_T=\frac{kT}{q}
\]

and \(N\) is a constant,

\[
V_{R1}=V_T\ln(N)
\]

is directly proportional to absolute temperature.

Hence,

\[
\boxed{V_{R1}\propto T}
\]

Therefore, the voltage across \(R_1\) is a **PTAT voltage**.

---

## 2. Temperature Dependence

The thermal voltage is given by

\[
V_T=\frac{kT}{q}
\]

where:

- \(k\) = Boltzmann constant
- \(T\) = absolute temperature in Kelvin
- \(q\) = electron charge

Therefore,

\[
\frac{dV_T}{dT}=\frac{k}{q}
\]

and

\[
\boxed{\frac{dV_T}{dT}\approx86\ \mu V/K}
\]

Thus, thermal voltage increases linearly with temperature.

### Nature of Different Voltages

| Voltage | Temperature Dependence |
|---|---|
| \(V\) | CTAT, with a smaller negative slope |
| \(V_1\) | CTAT, with a larger negative slope |
| \(V-V_1\) | PTAT |

Therefore,

\[
\boxed{V-V_1=V_T\ln(N)}
\]

is the required PTAT voltage.

---

# 3. Design of \(R_1\)

The value of \(R_1\) is selected based on the **power consumption** and **silicon area** available for the circuit.

![Design of R1 Resistance](https://github.com/user-attachments/assets/59cac808-e5de-4532-a83e-9ab3f6a909c9)

The voltage across \(R_1\) is

\[
V_{R1}=V_T\ln(N)
\]

Since the current through \(R_1\) is \(I\),

\[
V_{R1}=IR_1
\]

Therefore,

\[
\boxed{R_1=\frac{V_T\ln(N)}{I}}
\]

### Effect of Current on \(R_1\)

From the equation above:

- Increasing \(I\) decreases \(R_1\).
- Decreasing \(I\) increases \(R_1\).

A smaller resistance generally requires **less silicon area**, while a larger resistance requires **more silicon area**.

However, increasing the current also increases the **power consumption** of the circuit.

Therefore, there is a trade-off between **power consumption and resistor area**.

### Effect of BJT Area Ratio \(N\)

The resistance also depends on the area ratio \(N\):

\[
R_1\propto\ln(N)
\]

Therefore, increasing \(N\) increases \(\ln(N)\), which increases the required value of \(R_1\).

---

## Example Calculation

Consider:

\[
I=10\ \mu A
\]

and

\[
N=8
\]

At room temperature,

\[
V_T\approx26\ mV
\]

Therefore,

\[
R_1=
\frac{26\ mV\times\ln(8)}
{10\ \mu A}
\]

Since

\[
\ln(8)\approx2.079
\]

we get

\[
R_1\approx
\frac{26\times2.079\ mV}
{10\ \mu A}
\]

\[
\boxed{R_1\approx5.4\ k\Omega}
\]

---

## Key Takeaways

- Two diode-connected BJTs with an area ratio of **1:N** can generate a PTAT voltage.
- The voltage difference between the two BJTs is

\[
\boxed{\Delta V_{BE}=V_T\ln(N)}
\]

- Since \(V_T=kT/q\), the voltage difference is **PTAT**.
- The PTAT voltage appears across \(R_1\).
- The resistor value is

\[
\boxed{R_1=\frac{V_T\ln(N)}{I}}
\]

- Increasing current → smaller \(R_1\) → smaller resistor area but higher power consumption.
- Decreasing current → larger \(R_1\) → larger resistor area but lower power consumption.
- Increasing \(N\) → larger \(\ln(N)\) → larger \(R_1\).
- For \(I=10\,\mu A\) and \(N=8\), \(R_1\approx5.4\,k\Omega\).

---

## Summary

The key idea behind PTAT generation is to use two BJTs with different emitter areas while forcing the same current through them. The difference in their base-emitter voltages produces

\[
\boxed{\Delta V_{BE}=V_T\ln(N)}
\]

Since \(V_T\) is proportional to absolute temperature, \(\Delta V_{BE}\) is also proportional to temperature. This PTAT voltage can then be used in a **Bandgap Reference (BGR)** to compensate for the CTAT behavior of \(V_{BE}\).
