# Anenji-12KW-48V-Hybrid-split-phas
This guide shows the recommended wiring to read/control an Anenji 12kW split-phase inverter via Modbus RTU over RS485 using the Waveshare ESP32-S3 RS485/CAN DIN rail board.
---

## What you need

- **Anenji 12kW split-phase inverter** (RS485 Modbus capable)
- **Waveshare ESP32-S3 RS485/CAN DIN rail board**
- 1× twisted pair cable (shielded recommended) for RS485 A/B
- 1× ground wire (GND reference)
- Optional: 120Ω termination resistor (only if needed, see below)
- Power for the Waveshare board (recommended: **USB-C power brick** or a dedicated 5V supply)

---

## Recommended connection (3 wires)

### Connect inverter RS485 → Waveshare RS485

| Inverter RS485 | Waveshare RS485 terminal | Notes |
|---|---|---|
| **RS485 A / RS485+ / D+** | **A+ / 485A** | Differential “A/+” line |
| **RS485 B / RS485- / D-** | **B- / 485B** | Differential “B/−” line |
| **GND** | **GND** | Common reference (recommended) |

✅ That’s it: **A, B, GND**.

---

## Wiring diagram
ANENJI 12kW RS485 PORT WAVESHARE ESP32-S3 RS485/CAN (DIN)

RS485+ (A / D+) -----------------> A+ (485A)
RS485- (B / D-) -----------------> B- (485B)
GND -----------------> GND
