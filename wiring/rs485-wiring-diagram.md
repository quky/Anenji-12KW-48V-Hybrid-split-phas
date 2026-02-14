
---

## Powering the Waveshare board (recommended)

### Best option: USB-C power brick
- Use a stable **USB-C 5V** supply (phone charger is perfect).
- This avoids noise and keeps the comms stable.

### Notes on using inverter “5V” pins
Some inverter comm/ports expose **5V** pins (often for their own dongle).  
**Recommendation:** do **not** rely on inverter 5V unless you have verified:
- it can supply enough current continuously,
- it is isolated the way you expect,
- it remains stable during inverter mode changes.

If you do use inverter 5V, still connect RS485 GND to ESP GND.

---

## RS485 “A/B swapped” (common issue)

Different vendors label RS485 lines differently. If you see **timeouts / no data**:

1. Power down inverter comm connection (or unplug RS485).
2. **Swap A and B** at the Waveshare terminal:
   - inverter A → Waveshare B
   - inverter B → Waveshare A
3. Try again.

Symptoms of swapped A/B:
- ESPHome connects to WiFi fine, but Modbus reads show timeouts or no updates.

---

## Cable recommendations

- Use a **twisted pair** for A/B (CAT5/6 pair works great).
- Keep RS485 wiring away from high-current AC lines and inverter output cables.
- If inside a noisy electrical panel: use **shielded twisted pair**.
- If using shielded cable:
  - connect shield to ground **at one end only** (usually inverter side) to avoid ground loops.

---

## Termination resistor (only if needed)

RS485 termination is usually **not needed** for short runs.

Add a **120Ω resistor across A and B** only if:
- cable run is long (rule of thumb: **> 20 meters / 65 ft**), or
- you have repeated comm errors in a noisy environment, or
- multiple RS485 devices share the bus.

**Important:**
- Terminate **at one end only** for point-to-point runs.
- If you terminate at both ends, do so only when the bus is truly multi-drop and designed that way.

---

## ESPHome pin mapping (Waveshare DIN board)

This project uses the Waveshare board’s RS485 UART and driver enable:

- **TX:** GPIO17  
- **RX:** GPIO18  
- **RS485 EN (DE/RE):** GPIO21

(These match the Waveshare ESP32-S3 RS485/CAN DIN rail board documentation/pinout.)

---

## Quick validation checklist

Before blaming software, confirm:

- [ ] A/B/GND connected as above
- [ ] ESP32 powered from a stable source (USB-C recommended)
- [ ] Inverter RS485 port is the correct one (not CAN/BMS-only port)
- [ ] Modbus settings match inverter:
  - address typically `0x01`
  - baud typically `9600`
  - parity `NONE`
  - stop bits `1`
- [ ] If no data: swapped A/B test performed

---

## What “working” looks like in ESPHome logs

When wiring is correct, you’ll see periodic updates like:

- `Sensor new state: ...`
- values for PV/load/grid/battery updating every few seconds

If wiring is wrong (or A/B swapped), you’ll typically see:
- timeouts
- no sensor updates
- repeated retry behavior

---

## Safety notes

- RS485 is low voltage, but it is installed near high-energy equipment.
- Always route/secure wiring cleanly in the panel.
- Use ferrules for terminal connections where possible.
- Avoid sharing power/ground paths with high-current cables.

---

## Troubleshooting (fast)

1. **No readings at all**
   - Swap A/B
   - Verify inverter Modbus address
   - Confirm you’re on an RS485 Modbus port (not CAN-only)

2. **Intermittent readings**
   - Add GND reference wire
   - Shorten cable / re-route away from AC
   - Consider shielded cable
   - Consider 120Ω termination if long run

3. **Random spikes / unstable**
   - Use USB-C power brick for ESP
   - Ensure RS485 cable is twisted pair
   - Ensure shield is grounded at one end only

---

## Photos

Add photos to help others replicate:

- `wiring/photos/rs485-port-on-inverter.jpg`
- `wiring/photos/waveshare-terminal-block.jpg`
- `wiring/photos/din-rail-install.jpg`
- `wiring/photos/overall-panel.jpg`

If you share your photos, keep serial numbers and private network details out of frame.
