# Day 5: Reference Branch Circuit

## Concepts Covered

1. Introduction to the reference branch circuit
2. Design of R2

## Reference Branch Circuit

<img width="1055" height="866" alt="image" src="https://github.com/user-attachments/assets/866aa50b-acb5-4972-b955-577a0a557eec" />

### Reference Branch of the BGR

The **reference branch** is the third branch of the BGR. It combines the **CTAT and PTAT voltages** generated earlier to produce the final reference voltage $V_{ref}$.

* $M_{P3}$ mirrors the bias current into this branch, so $I_3 = I_1 = I_2$.
* $I_3$ flows through $R_2$ and the diode-connected BJT $Q_3$.
* $V_{ref}$ is taken at the top of $R_2$.
* $V_{BE3}$ is **CTAT**.
* The voltage across $R_2$ is **PTAT**.
* $R_2=\alpha R_1$.

Therefore,

$$
V_{ref}=V_{BE3}+I_3R_2
$$

Since

$$
I_3=\frac{V_T\ln(N)}{R_1}
$$

and

$$
R_2=\alpha R_1
$$

we get

$$
V_{ref}
=V_{BE3}
+\frac{V_T\ln(N)}{R_1}(\alpha R_1)
$$

Hence,

$$
\boxed{V_{ref}=V_{BE3}+\alpha V_T\ln(N)}
$$

## Design of R2 Resistance

<img width="943" height="473" alt="image" src="https://github.com/user-attachments/assets/f2650bac-c001-4011-9d6d-44d77ce591e4" />

For a temperature-independent reference voltage, the **temperature coefficient of $V_{ref}$ should be zero**:

$$
\frac{dV_{ref}}{dT}=0
$$

Since

$$
V_{ref}=V_{Q3}+V_{R2}
$$

we require

$$
\frac{dV_{R2}}{dT}+\frac{dV_{Q3}}{dT}=0
$$

Given:

* $\frac{dV_{Q3}}{dT}=-1.6\,\text{mV}/^\circ\text{C}$
* $\frac{dV_T}{dT}=85\,\mu\text{V}/^\circ\text{C}$
* $V_{R2}=\alpha V_T\ln(N)$

Therefore,

$$
\alpha\ln(N)\frac{dV_T}{dT}+\frac{dV_{Q3}}{dT}=0
$$

So,

$$
\alpha\ln(N)
=\frac{1.6\,\text{mV}}{85\,\mu\text{V}}
\approx18.8
$$

For $N=8$,

$$
\ln(8)\approx2.08
$$

Hence,

$$
\alpha=\frac{18.8}{2.08}\approx9
$$

Therefore,

$$
\boxed{\alpha\approx9}
$$

and since

$$
R_2=\alpha R_1
$$

we get

$$
\boxed{R_2\approx9R_1}
$$

## Lab

Will be added soon.
