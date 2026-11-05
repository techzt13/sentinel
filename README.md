# Sentinel

*A pocket guardian for your smart home — a DIY Flipper-Zero-style multi-tool built on the **M5Stack Cardputer ADV (ESP32-S3)**.*

Dual-booting:

- **Evil-M5Project** — WiFi security testing (scanning, captive portals, handshake capture, wardriving, BadUSB)
- **Bruce** — NFC/RFID, Sub-GHz RF, 2.4 GHz, IR, BLE utilities

> ⚠️ **Legal / ethical use only.** Every offensive feature in this build is used **only against networks, devices, cards, and remotes I own**. See [docs/rules.md](docs/rules.md).

## Hardware (~$145)

| Part | Price | Purpose |
| --- | --- | --- |
| M5Stack Cardputer ADV (ESP32-S3) | $29.90 | Main unit — keyboard, screen, camera, mic, WiFi/BLE |
| Hydra RF 424 (CC1101 + nRF24L01+, 433 MHz) | $34.99 | Sub-GHz 433 MHz + 2.4 GHz expansion (antennas included) |
| PN532 NFC/RFID V3 module | ~$7 | NFC 13.56 MHz read/write/emulate (Grove, I2C mode) |
| RDM6300 125 kHz RFID reader | ~$3.60 | Older badges/key fobs — the gap a stock Flipper covers |
| GPS/BDS Unit (AT6668) + SMA antenna | $12.50 | Wardriving with Wigle-compatible CSV output |
| Grove LoRa-E5 (STM32WLE5JC) | ~$9.90 | LoRa / Meshtastic off-grid mesh — beyond Flipper |
| ENV Pro (BME688) | ~$24.50 | Temp/humidity/pressure/air-quality — smart-home monitoring |
| ToF Sensor Unit (VL53L0X) | ~$8.50 | Laser distance — presence/proximity detection |
| Mini Infrared Emitter & Receiver Unit | $3.95 | IR capture/learning |
| Grove cables (2× 5-pack) + microSD 16 GB | ~$10 | Wiring + storage (required by firmwares) |

Full details with links, notes and a dropped-items decision log: [bom.md](bom.md)

**Pin-budget note:** the ADV has limited free GPIO, and top-mounted RF boards occupy the
pins the GPS unit needs. Nothing is soldered, so Sentinel runs in **two configurations**:
RF/NFC sessions (Hydra + Grove devices) and wardriving sessions (Hydra off + GPS).

## Capability map

| Capability | Handled by |
| --- | --- |
| WiFi scan / portals / handshakes / wardriving | Evil-M5Project (built-in WiFi) |
| BLE tools | Bruce (built-in BLE) |
| NFC read / write / emulate (13.56 MHz) | Bruce + PN532 (I2C) |
| 125 kHz RFID read (EM4100) | Bruce + RDM6300 (UART) |
| Sub-GHz 433 MHz RX/TX | Bruce + Hydra (CC1101) |
| 2.4 GHz scanning | Bruce + Hydra (nRF24L01+) |
| LoRa / Meshtastic mesh | Grove LoRa-E5 (UART, AS923) |
| IR blast + code learning | Built-in emitter + IR unit |
| GPS wardriving / position | GPS unit (Hydra-off session) |
| Air quality / environment | ENV Pro BME688 (I2C) |
| Presence / distance | ToF VL53L0X (I2C) |
| BadUSB keystroke injection | Both firmwares (own machines only) |

## Docs

- [Pitch](docs/pitch.md) — why someone would buy Sentinel (smart-home lead angle)
- [Setup guide](docs/setup-guide.md) — SD prep → M5Launcher → firmwares → Hydra/PN532 → first tests
- [Project ideas](docs/project-ideas.md) — what this build can actually do
- [Rules](docs/rules.md) — the non-negotiables

## Sources

- Evil-M5Project: https://github.com/7h30th3r0n3/Evil-M5Project
- Bruce: https://github.com/pr3y/Bruce
- M5Launcher: https://github.com/bmorcelli/M5Stick-Launcher (search "M5Launcher")
- Hydra RF 424: https://www.pingequa.com/products/cardputer-adv-hydra-rf-424
