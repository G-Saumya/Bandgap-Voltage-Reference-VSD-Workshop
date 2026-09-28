Day 6: Start-up Circuit
Concepts covered: 
1) Why a start-up circuit is needed in a self-biased current mirror.
2) How the start-up circuit works.

Why Start-up?
<img width="961" height="512" alt="image" src="https://github.com/user-attachments/assets/4b0297b4-8302-4fe0-ac5d-9a538b23efe6" />
### Start-Up Problem in the Self-Biased Current Mirror

A self-biased current mirror has a **degenerate operating point** where all transistors are OFF. In this state, no current flows, so the circuit cannot move out of the zero-current state by itself. This is called the **start-up problem**.

To solve this, a **start-up circuit** consisting of \(M_{P4}\), \(M_{P5}\), and \(M_{N3}\) is added to the BGR.

* At power-up, it injects a small current into the core circuit.
* This forces the circuit away from the zero-current state.
* Once the circuit reaches its intended operating point, the start-up circuit becomes inactive.

## Working of the Start-Up Circuit

* Initially, the circuit current is zero, so **net2 is at \(V_{DD}\)**.
* When net2 becomes approximately one \(V_T\) above net6, \(M_{P5}\) turns ON.
* \(M_{P5}\) pulls **net1 upward**, providing the initial current needed to start the circuit.
* As net1 rises, **\(M_{N1}\) and \(M_{N2}\)** turn ON.
* The self-biased loop then starts conducting and moves to its **normal operating point**.

## Start-Up Circuit Turns OFF

Once the self-biased loop is running, the **net2 voltage decreases**.

When net2 is no longer sufficiently high relative to net6 to keep \(M_{P5}\) ON, \(M_{P5}\) turns OFF.
