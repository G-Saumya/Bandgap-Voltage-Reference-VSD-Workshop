# Day 8: Complete BGR Pre-layout Simulation (Lab 7 Component)

## Concepts Covered

1. Process corners (tt, ff, ss)
2. Pre-layout simulation of the complete bandgap voltage reference across these corners

## Process Corners: TT, FF, and SS

Manufacturing variations cause transistor parameters to differ slightly from their nominal values. These variations are represented using process corners, which model different extremes of the fabrication process.

The two letters indicate the NMOS and PMOS process conditions:

| Corner | NMOS | PMOS | Meaning |
|--------|------|------|---------|
| TT | Typical | Typical | Nominal process |
| FF | Fast | Fast | Both devices are faster than nominal |
| SS | Slow | Slow | Both devices are slower than nominal |

- **FF:** Typically has lower $V_{TH}$ and higher carrier mobility, resulting in higher current for the same bias.
- **SS:** Typically has higher $V_{TH}$ and lower carrier mobility, resulting in lower current for the same bias.

Other combinations such as FS and SF are called skewed corners, but they are not considered in this lab.

## Why Process Corners Matter in a BGR

A BGR should remain stable despite PVT (Process, Voltage, and Temperature) variations. Therefore, it must be tested across different process corners.

Changes in transistor, resistor, and BJT parameters can affect the bias current and the CTAT–PTAT cancellation, causing changes in the $V_{ref}$ vs. temperature curve.

The simulations below compare the BGR's $V_{ref}$ across the TT, FF, and SS process corners.

## Lab 7: Process Corner Analysis

### Circuit

The circuit used for the simulation is shown below.

<img width="862" height="627" alt="Lab 7 circuit" src="https://github.com/user-attachments/assets/3d29a9ee-c925-4cfd-bfbc-680a39751cb3" />

### SPICE Code: DC Simulation Across tt, ff, and ss Corners
<img width="891" height="665" alt="image" src="https://github.com/user-attachments/assets/5c180b6b-7660-4995-91b1-3f0c2d40b951" />
<img width="832" height="598" alt="image" src="https://github.com/user-attachments/assets/13ff2377-c994-4a63-83fd-cfd2863d06a1" />
<img width="908" height="233" alt="image" src="https://github.com/user-attachments/assets/4e6a1f34-0151-47c7-9f2d-b0a82306affd" />

DC simulation: tt vs ff vs ss corner
#### tt Corner

<img width="1597" height="867" alt="tt corner SPICE code" src="https://github.com/user-attachments/assets/db5a93df-615b-48fe-90db-cd16b164540b" />

<img width="1517" height="715" alt="tt corner response" src="https://github.com/user-attachments/assets/ae6b6d06-db49-4296-bde8-2a07bcc8472f" />

From the graph:

- $V_{max}\approx 1.10996\,V$ at around $25^\circ C$
- $V_{min}\approx 1.1057\,V$ at $-40^\circ C$
- Temperature range: $-40^\circ C$ to $125^\circ C$
- $V_{nom}\approx1.109\,V$

Using the usual overall temperature coefficient:

$$
TC=\frac{V_{max}-V_{min}}{V_{nom}(T_{max}-T_{min})}\times10^6
$$

$$
TC\approx\frac{0.00426}{182.985}\times10^6
$$

$$
\boxed{TC\approx23.3\ ppm/^\circ C}
$$

#### ff Corner

<img width="1841" height="891" alt="ff corner response" src="https://github.com/user-attachments/assets/84d19052-4221-4f25-81fc-348e59a6c512" />

- $V_{max}\approx1.12226\,V$
- $V_{min}\approx 1.12040\,V$
- Temperature range: $-40^\circ C$ to $125^\circ C$
- $V_{nom}\approx 1.1213\,V$

Using

$$
TC=\frac{V_{\max}-V_{\min}} {V_{nom}(T_{\max}-T_{\min})}\times10^6
$$

$$
\boxed{TC\approx10.1\ ppm/^\circ C}
$$

#### ss Corner

<img width="1848" height="878" alt="ss corner response" src="https://github.com/user-attachments/assets/16fca4a6-f232-4da4-a2c9-0295504eec0f" />

The temperature coefficient for this corner is **45 ppm/°C**.

### Summary

| Corner | Temperature Coefficient |
|--------|--------------------------|
| tt | 23.3 ppm/°C |
| ff | 10.1 ppm/°C |
| ss | 45 ppm/°C |
