# 🔋 Anenji 12kW Split-Phase Inverter  
## ESPHome Modbus RS485 Integration for Home Assistant

Professional, open-source integration for the **Anenji 12kW Split-Phase (48V)** inverter using:

- 🧠 ESPHome  
- 🔌 Modbus RTU (RS485)  
- 📊 Home Assistant Energy Dashboard  
- 🏠 Full inverter control  

Designed specifically for:
> **Anenji 12kW Split-Phase models with RS485 Modbus port**

---

# ✨ Features

## 📊 Live Monitoring
- PV Power (per MPPT + total)
- Load Power (L1, L2, Total)
- Grid Import / Export (CT grid-side)
- Battery Voltage / Current / SOC
- Battery Charge & Discharge Power
- Output Voltage & Frequency

## ⚡ Energy Dashboard Compatible
- PV Energy (daily kWh)
- Load Energy (daily kWh)
- Grid Import / Export Energy
- Battery Charge / Discharge Energy

Fully compatible with:
> Home Assistant Energy Dashboard

---

## 🎛 Inverter Controls

- ✅ AC Output On / Off
- ✅ Charging Priority (dropdown)
- ✅ Load Output Priority (dropdown)
- ✅ Restart Inverter
- ✅ Enforce Zero Export (A089 = 0)
- ✅ Disable Grid Feed-in (A088)

---

# 🧰 Hardware Required

## 1️⃣ Inverter
- **Anenji 12kW Split-Phase**
- Must have RS485 Modbus communication port

## 2️⃣ Communication Board
- **Waveshare ESP32-S3 RS485/CAN DIN Rail**

## 3️⃣ Wiring
- Twisted pair (A/B)
- Ground reference wire
- Optional 120Ω resistor (long runs only)

---

# 🔌 RS485 Wiring

See full wiring guide here:
📁 [`wiring/rs485-wiring-diagram.md`](https://github.com/quky/Anenji-12KW-48V-Hybrid-split-phas/blob/main/wiring/rs485-wiring-diagram.md))

### Basic Connection

| Inverter RS485 | Waveshare RS485 |
|---------------|----------------|
| RS485+ (A) | A+ |
| RS485- (B) | B- |
| GND | GND |

If communication fails:
> Swap A and B.

---

# ⚙️ ESPHome Configuration

Main config file:

