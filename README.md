# Sentinel

*A pocket guardian for your smart home — a DIY Flipper-Zero-style multi-tool built on the **M5Stack Cardputer ADV (ESP32-S3)**.*

Dual-booting:

- **Evil-M5Project** — WiFi security testing (scanning, captive portals, handshake capture, wardriving, BadUSB)
- **Bruce** — NFC/RFID, Sub-GHz RF, 2.4 GHz, IR, BLE utilities

Managed by **M5Launcher** so either firmware can be booted from the SD card.

> ⚠️ **Legal / ethical use only.** Every offensive feature in this build is used **only against networks, devices, cards, and remotes I own**. See [docs/rules.md](docs/rules.md).

## Hardware (~$93)

| Part | Price | Purpose |
| --- | --- | --- |
| M5Stack Cardputer ADV (ESP32-S3) | $29.90 | Main unit — keyboard, screen, IR emitter, WiFi/BLE |
| Hydra RF 424 (CC1101 + nRF24L01+, 433 MHz) | $34.99 | Sub-GHz 433 MHz + 2.4 GHz expansion (Pingequa) |
| PN532 NFC/RFID V3 module | ~$7 | NFC 13.56 MHz read/write/emulate (Grove, I2C mode) |
| GPS/BDS Unit (AT6668) + SMA antenna | $12.50 | Wardriving with Wigle-compatible CSV output |
| Mini Infrared Emitter & Receiver Unit | $3.95 | IR capture/learning |
| SanDisk Ultra microSD 16 GB, FAT32 (SDHC) | ~$5 | **Required** by both firmwares |

Full details with links: [bom.csv](bom.csv)

**Pin-budget note:** the ADV has limited free GPIO, and top-mounted RF boards occupy the
pins the GPS unit needs. Nothing is soldered, so Sentinel runs in **two configurations**:
RF/NFC sessions (Hydra + PN532) and wardriving sessions (Hydra off + GPS).

**Known gap vs. a real Flipper Zero:** no 125 kHz RFID (older key fobs/badges).

## Capability map

| Capability | Handled by |
| --- | --- |
| WiFi scan / portals / handshakes / wardriving | Evil-M5Project (built-in WiFi) |
| NFC read / write / emulate (13.56 MHz) | Bruce + PN532 (I2C) |
| Sub-GHz 433 MHz RX/TX | Bruce + Hydra (CC1101) |
| 2.4 GHz scanning | Bruce + Hydra (nRF24L01+) |
| IR blast + code learning | Built-in emitter + IR unit |
| BadUSB keystroke injection | Both firmwares (own machines only) |
| GPS wardriving | Evil-M5Project + GPS unit (Hydra-off session) |

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
