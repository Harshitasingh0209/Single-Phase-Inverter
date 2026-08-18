# Single-Phase SPWM Inverter (220V AC Output)

A microcontroller-based single-phase inverter system utilizing **Sinusoidal Pulse Width Modulation (SPWM)** to convert direct current (DC) into a clean alternating current (AC) output at 220V, 50 Hz.
---
## **Project Overview**

This project demonstrates the design and implementation of a single-phase H-bridge inverter controlled by SPWM signals. The system uses precomputed lookup tables for low-overhead sine wave generation, driving complementary power switches (MOSFETs) through high/low side gate drivers.

* **DC Input:** Battery / Power Supply
* **AC Output:** 220V AC RMS, 50 Hz Pure Sine Wave (after filtering)
* **Switching Topology:** Single-Phase Full-Bridge (H-Bridge)
* **Control Technique:** Microcontroller-generated SPWM

---

## **Hardware Architecture & Components**

* **Microcontroller:** Arduino / ATmega328P (Generates SPWM control signals)
* **Gate Driver IC:** IR2110 / IR2113 with bootstrap circuit for high-side driving
* **Power MOSFETs:** 4x Power MOSFETs (e.g., IRF840 / IRFP460) in Full-Bridge configuration
* **Output Filter:** Low-Pass LC Filter ($L_{filter}$, $C_{filter}$) to eliminate high-frequency switching harmonics
* **Step-Up Transformer:** Transformer to step up filtered AC output to 220V RMS

---

## **Hardware Setup & Pinout**

| Component Pin | MCU Pin | Function |
| :--- | :--- | :--- |
| **Gate Driver 1 (HIN/LIN)** | Pin 10 | Upper MOSFET Branch Control Signal |
| **Gate Driver 2 (HIN/LIN)** | Pin 9 | Lower MOSFET Branch Control Signal |
| **GND** | GND | Common System Ground Reference |

> **Safety Warning:** High voltage (220V AC) is generated during operation. Ensure proper isolation between control and power circuits, adequate dead-time insertion to prevent shoot-through currents, and proper heat sinking for power MOSFETs.

---

## **Getting Started**

1. Connect pins **9** and **10** of the microcontroller to your gate driver input channels.
2. Wire the driver outputs directly to the MOSFET gates on the H-bridge power stage.
3. Pass the H-bridge output through the LC filter before feeding it into the step-up transformer.
4. Flash the controller software and verify output waveforms using an oscilloscope.
