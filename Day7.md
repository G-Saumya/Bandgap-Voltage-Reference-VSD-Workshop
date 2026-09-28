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
* **Day 2:** $V_{BE}$ of a BJT provides the **CTAT** voltage.
* **Day 3:** Two BJTs with $1:N$ area ratio generate **PTAT** voltage: $\Delta V_{BE}=V_T\ln(N)$
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

## Lab

*To be added soon.*
