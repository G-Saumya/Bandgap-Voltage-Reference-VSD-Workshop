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

## 2. Applications of BGR

### Low Dropout Regulators (LDO)
<p align="center">
  <img width="532" height="535" alt="LDO" src="https://github.com/user-attachments/assets/9d6f1632-7ee8-4b5e-8198-8158604ba1c3" />
</p>

### DC-DC Buck Converters
<p align="center">
  <img width="660" height="542" alt="DC-DC Buck Converter" src="https://github.com/user-attachments/assets/baad1f9b-41d5-4ebf-b613-0db0a2232b4f" />
</p>

### Analog to Digital Converters (ADC)
<p align="center">
  <img width="547" height="593" alt="ADC" src="https://github.com/user-attachments/assets/f76f1b7e-0b4f-48da-8e63-584a0c15d882" />
</p>

### Digital to Analog Converters (DAC)
<p align="center">
  <img width="722" height="412" alt="DAC" src="https://github.com/user-attachments/assets/922243a8-84bf-443a-924d-dabfe69449a1" />
</p>

---

## 3. Principle of BGR

A BGR cancels two opposite temperature effects to get a temperature-independent voltage:

- **CTAT:** the base-emitter voltage of a BJT falls as temperature rises (about -2 mV/°C).
- **PTAT:** the difference between the base-emitter voltages of two BJTs operating at different current densities rises in direct proportion to absolute temperature.

The PTAT voltage is scaled by a suitable factor and added to the CTAT voltage. The factor is chosen so the two temperature slopes cancel, giving an output of about **1.2 V**, close to the silicon bandgap voltage, that stays nearly constant across temperature.

<p align="center">
  <img width="768" height="495" alt="Principle of BGR" src="https://github.com/user-attachments/assets/4f58e093-a6e3-47f3-a608-b40e8bccfa27" />
</p>

---

## 4. Types of BGR

<p align="center">
  <img width="808" height="507" alt="Types of BGR" src="https://github.com/user-attachments/assets/271d8fd7-3fef-48b3-aa5c-ba3aebbce7d0" />
</p>

---

## 5. Self-biased Current Mirror based BGR: Advantages and Limitations

<p align="center">
  <img width="727" height="477" alt="Self-biased current mirror BGR" src="https://github.com/user-attachments/assets/587855c3-90cd-41c7-b30c-aad62c339f1d" />
</p>

---

## 6. Components of BGR

<p align="center">
  <img width="707" height="373" alt="Components of BGR" src="https://github.com/user-attachments/assets/68fc2a49-c6e7-45f7-ad01-43ac05582d6b" />
</p>
