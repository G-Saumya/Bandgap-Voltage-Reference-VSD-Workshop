# Day 1: Introduction to Bandgap Voltage Reference

## Concepts Covered

1. Introduction to Bandgap Voltage Reference
2. Applications of BGR
3. Principles of BGR
4. Types of BGR
5. Self-biased current mirror based BGR: advantages and limitations
6. Components of BGR

---

## 1. Introduction to Bandgap Voltage Reference

A **bandgap voltage reference (BGR)** is an analog circuit that produces a stable DC voltage, typically around **1.2 V**, that stays nearly constant despite changes in temperature, supply voltage, and process variation.

It works by combining two voltages with opposite temperature behavior:

- **CTAT** (Complementary to Absolute Temperature): a voltage that falls as temperature rises.
- **PTAT** (Proportional to Absolute Temperature): a voltage that rises with temperature.

---

## Why BGR?

Every analog and mixed-signal system needs a stable reference voltage, but the obvious sources each fall short:

- **Battery:** its voltage drops steadily over the course of its usage, so it cannot provide a fixed reference.
- **Power supply:** the output is noisy and carries ripple, and it varies with load and line conditions.
- **Zener diode reference IC:** it is a workable option, but it is an external component, needs additional resistors and capacitors to set or change the voltage, and is not suitable for low-voltage applications because Zener breakdown typically occurs at several volts.

**A BGR overcomes these limitations.**

<p align="center">
  <img width="870" height="492" alt="Why BGR" src="https://github.com/user-attachments/assets/24e0e45c-720f-46a5-a10d-b59a3d7f0c36" />
</p>

---

## 2.
