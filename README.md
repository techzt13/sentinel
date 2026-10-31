# Cardputer "Flipper-Style" Build

A DIY Flipper-Zero-style multi-tool built on the **M5Stack Cardputer ADV (ESP32-S3)**, dual-booting:

- **Evil-M5Project** — WiFi security testing (scanning, captive portals, handshake capture, wardriving, BadUSB)
- **Bruce** — NFC/RFID, Sub-GHz RF, IR, BLE utilities

Managed by **M5Launcher** so either firmware can be booted from the SD card.

> ⚠️ **Legal / ethical use only.** Every offensive feature in this build is used **only against networks, devices, cards, and remotes I own**. See [docs/rules.md](docs/rules.md).

## Hardware

| Part | Price | Purpose |
| --- | --- | --- |
| M5Stack Cardputer ADV (ESP32-S3) | $29.90 | Main unit — keyboard, screen, IR emitter, WiFi/BLE |
| Cap CC1101 & NFC for Cardputer Adv (U219) | $18.95 | Sub-GHz 315/433/868/915 MHz + NFC (ST25R3916, FeliCa + card emulation) |
| GPS/BDS Unit (AT6668) + SMA antenna | $12.50 | Wardriving with Wigle-compatible CSV output |
| Mini Infrared Emitter & Receiver Unit | $3.95 | IR capture/learning |
| I2C Hub 1-to-6 (PCA9548A) | $5.95 | Grove expansion for future I2C add-ons |
| Connector Grove to 4 Pin (10 pcs) | $4.50 | Wiring adapters |
| microSD 8–16 GB, FAT32 (SDHC) | ~$5 | **Required** by both firmwares |

**Total: ~$81.** All from the M5Stack official store (ships from Shenzhen — fast to Hong Kong).

**Known gap vs. a real Flipper Zero:** no 125 kHz RFID (older key fobs/badges).

## Capability map

| Capability | Handled by |
| --- | --- |
| WiFi scan / portals / handshakes / wardriving | Evil-M5Project (built-in WiFi) |
| NFC read / write / emulate (13.56 MHz, FeliCa) | Bruce + Cap (ST25R3916) |
| Sub-GHz 315/433/868/915 MHz RX/TX | Bruce + Cap (CC1101) |
| IR blast + code learning | Built-in emitter + IR unit |
| BadUSB keystroke injection | Both firmwares (own machines only) |
| GPS wardriving | Evil-M5Project + GPS unit |

## Docs

- [Setup guide](docs/setup-guide.md) — SD prep → M5Launcher → firmwares → Cap → first tests
- [Project ideas](docs/project-ideas.md) — what this build can actually do
- [Rules](docs/rules.md) — the non-negotiables

## Sources

- Evil-M5Project: https://github.com/7h30th3r0n3/Evil-M5Project
- Bruce: https://github.com/pr3y/Bruce
- M5Launcher: https://github.com/bmorcelli/M5Stick-Launcher (search "M5Launcher")
