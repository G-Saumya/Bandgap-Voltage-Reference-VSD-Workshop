# Day 4: Self-Biased Current Mirror

## Concepts Covered

1. Self-biased current mirror: principle
2. Why self-bias
3. SPICE simulation in the lab

## Why a Self-Biased Current Mirror?

### Supply-Independent Current Generation

A reference generation circuit should ideally remain **independent of the supply voltage**, in addition to being insensitive to **process and temperature variations**.

The **temperature dependence** is addressed using the **CTAT and PTAT voltage generation circuits**. However, these circuits require a **constant and stable current** for proper operation.

Therefore, the generated current must also be made **independent of the supply voltage**. To achieve this, **CMOS current mirrors** are used to generate and distribute the required bias current while maintaining a relatively constant current despite variations in the supply voltage.

## Issues with Normal Current Mirrors

<img width="958" height="513" alt="image" src="https://github.com/user-attachments/assets/9f713e12-9503-4a8e-bcd6-a091ccc95ede" />

As observed earlier, the output current changes when the supply voltage varies. This dependence on the supply voltage is undesirable in a reference circuit.

To reduce the sensitivity, the circuit should be designed to bias itself.

## Self-Biased Current Mirror

<img width="611" height="515" alt="image" src="https://github.com/user-attachments/assets/92d80758-17f8-4cea-8395-e2027e042ead" />

### Bootstrapping of the Reference Current

In the topology shown above, the output current $I_{out}$ is mirrored to generate the reference current $I_{ref}$. The PMOS transistors $M_{P1}$ and $M_{P2}$ replicate $I_{out}$ and establish the required $I_{ref}$.

This technique of using the output current to generate the reference current is known as bootstrapping.

Since each diode-connected device is driven by a current source, both $I_{out}$ and $I_{ref}$ become relatively insensitive to variations in the supply voltage $V_{DD}$.

$$
\boxed{I_{out}\approx I_{ref}}
$$

## Issues with the Topology

1) The circuit can operate at any current value.
2) Start-up problem: The circuit may settle at the zero-current state.

### Solution to Issue 1

Add a resistor $R_S$ to $M_{N2}$ to establish a defined operating current.

<img width="606" height="583" alt="image" src="https://github.com/user-attachments/assets/a0826f15-42c2-46d5-a577-2f309d4013d5" />

The resistor $R_S$ sets a unique value of $I_{out}$. Since the circuit gain is less than 1, the circuit is stable.

Below is the equation for Iout in terms of Rs.

<img width="792" height="162" alt="image" src="https://github.com/user-attachments/assets/fde2baaf-bd6b-4e1b-8c37-635def340252" />

The second issue, the start-up problem, will be addressed later.

## Advantages and Limitations of the Self-Biased Current Mirror

<img width="957" height="458" alt="image" src="https://github.com/user-attachments/assets/54b9b3a4-5071-4d43-8fc8-1c8dbef5509e" />

