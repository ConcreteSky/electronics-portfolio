# Project 2.6 — Project Notes
**Smart Light-Activated Relay System with Arduino**  
**Murad Shirinov | Electronics & Embedded Systems | May 2025**

---

## What This Project Does
- Detects ambient light using an LDR sensor
- When it gets dark → Arduino activates relay → lamp turns ON + LED turns ON
- When light returns → relay turns OFF → lamp turns OFF + LED turns OFF

---

## Components Used

| Component | Value | Purpose |
|---|---|---|
| Arduino Uno | ATmega328P | Brain — reads sensor, controls outputs |
| LDR Sensor | Light-dependent | Detects light/dark |
| Resistor | 10 kΩ | Voltage divider with LDR |
| Relay Module | 5V SPDT | Switches high-power lamp safely |
| Flyback Diode | 1N4148 | Protects circuit from relay voltage spike |
| LED | Red | Visual indicator when relay is active |
| Resistor | 220 Ω | Protects LED from overcurrent |
| Lamp | AC load | Output load controlled by relay |

---

## Pin Connections

| Arduino Pin | Connected To |
|---|---|
| A0 | LDR sensor output |
| Pin 7 | Relay module IN |
| Pin 13 | LED (via 220Ω resistor) |
| 5V | LDR VCC + Relay VCC |
| GND | LDR GND + Relay GND + LED cathode |

---

## How The Code Works
- Reads LDR value every 100ms via `analogRead(A0)` → gives value between 0–1023
- Compares against threshold of **500**
- **Below 500** (dark) → Pin 7 HIGH + Pin 13 HIGH (relay + LED on)
- **Above 500** (bright) → Pin 7 LOW + Pin 13 LOW (relay + LED off)
- Threshold is a software variable — adjustable anytime without changing hardware

---

## How This Upgrades Project 2.5

| | Project 2.5 | Project 2.6 |
|---|---|---|
| Control | Analog transistor | Arduino microcontroller |
| Threshold | Fixed by resistors | Software variable |
| Feedback | None | LED indicator |
| Expandability | Limited | IoT/sensor ready |

---

## Simulation
Built and tested in **Wokwi** — [View Circuit](https://wokwi.com/projects/464434725672017921)

---

## Key Concepts Applied
- Analog-to-Digital Conversion (ADC)
- Threshold-based conditional logic
- Relay driving from microcontroller
- Flyback diode protection
- Voltage divider with LDR
