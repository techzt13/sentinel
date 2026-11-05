# Sentinel — Bill of Materials

Prices in USD. Items marked *approx* should be confirmed at checkout.

## Active build

| Part | SKU / Version | Qty | Unit price | Line total | Category | Purpose | Link | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| M5Stack Cardputer ADV (ESP32-S3) | K132-Adv | 1 | $29.90 | $29.90 | Core | Main unit — keyboard / screen / IR emitter / WiFi+BLE | [link](https://shop.m5stack.com/products/m5stack-cardputer-adv-version-esp32-s3?variant=46698741203201) | |
| Hydra RF 424 (CC1101 + nRF24L01+, 433 MHz) | Hydra-424 | 1 | $34.99 | $34.99 | Radio | Sub-GHz 433 MHz + 2.4 GHz expansion | [link](https://www.pingequa.com/products/cardputer-adv-hydra-rf-424) | 433 MHz ISM is correct for Hong Kong. Mounts on ADV top header. Antennas included. |
| PN532 NFC/RFID Module V3 (I2C/SPI) | Generic PN532 | 1 | $7.00 | $7.00 | NFC | NFC 13.56 MHz read/write/emulate | [link](https://www.aliexpress.com/item/1005006250619105.html) | Set DIP switches to I2C mode. Connects to Grove port. |
| GPS/BDS Unit + SMA antenna (AT6668) | U190 | 1 | $12.50 | $12.50 | Positioning | Wardriving with Wigle-compatible CSV output | [link](https://shop.m5stack.com/products/gps-bds-unit-with-sma-antenna-at6668?variant=45785400508673) | CONFLICT: top RF boards occupy G13/G15 — use GPS in "Hydra off" sessions only. |
| Mini Infrared Emitter & Receiver Unit | U002 | 1 | $3.95 | $3.95 | IR | IR capture/learning (ADV also has built-in emitter on G44) | [link](https://shop.m5stack.com/products/ir-unit?variant=16804756979802) | Receiver needs one free GPIO — separate session from PN532. |
| SanDisk Ultra microSDHC 16GB UHS-I A1 | SDSQUAR-016G | 1 | $5.00 | $5.00 | Storage | Required by both firmwares — evil/ folder + firmware .bins | [link](https://shop.pegasus.hk/products/217478) | SDHC 16 GB — format FAT32. |
| 125 kHz RFID Reader Module (RDM6300, UART) | Generic RDM6300 | 1 | ~$3.60 | ~$3.60 | RFID | 125 kHz read (EM4100 badges/fobs) — closes last gap vs Flipper Zero | [link](https://www.aliexpress.com/item/1740848208.html) | Bare header pins — connect via dupont/Grove pigtail. UART, session-swap. |
| 4Pin Buckled Grove Cable 20cm (5 pcs) | M5Stack cable | 2 | ~$2.50 | ~$5.00 | Wiring | Spare Grove cables — PN532 ships without one | [link](https://shop.m5stack.com/products/4pin-buckled-grove-cable?variant=32050917081178) | 2 packs. |
| ToF Sensor Unit (VL53L0X) | U010 | 1 | ~$8.50 | ~$8.50 | Sensor | Laser distance — presence/proximity detection for smart-home demos | [link](https://shop.m5stack.com/products/tof-sensor-unit?variant=16804759076954) | I2C on Grove port — shares bus with PN532. |
| ENV Pro Unit (BME688) | U001-B | 1 | ~$24.50 | ~$24.50 | Sensor | Temp / humidity / pressure / gas (VOC) — air-quality monitoring | [link](https://shop.m5stack.com/products/env-pro-unit-with-temperature-humidity-pressure-and-gas-sensor-bme688) | I2C on Grove port — shares bus with PN532/ToF. |
| Grove LoRa-E5 (STM32WLE5JC) | Seeed 113020091 | 1 | ~$9.90 | ~$9.90 | Radio | LoRa long-range — Meshtastic off-grid mesh (pairs with GPS) | [link](https://www.digikey.hk/en/products/detail/seeed-technology-co-ltd/113020091/13926232) | Grove UART (AT commands), session-swap. AS923 band plan for HK. |
| **TOTAL** | | | | **~$144.84** | | | | |

## Dropped items (and why)

| Part | Was | Why dropped |
| --- | --- | --- |
| I2C Hub 1-to-6 (PCA9548A) | [link](https://shop.m5stack.com/products/i2c-hub-1-to-6-expansion-unit-v2-1-with-dip-switch-pca9548a?variant=45809830953217) | I2C-only — cannot split UART (GPS) or GPIO (IR) signals. Only useful for future pure-I2C sensors. |
| Connector Grove to 4 Pin (10 pcs) | [link](https://shop.m5stack.com/products/connector-grove-to-4-pin-10pcs?variant=39414310437036) | Passive adapters; M5 units ship with their own Grove cables. |
| M5Stack LoRa Module 13.2 (SX1262) | [link](https://shop.m5stack.com/products/lora-module-13-2-sx1262) | M5-Bus stackable module — Cardputer has no M5-Bus port. Replaced by Grove LoRa-E5. |
| Seeed Grove 125 kHz RFID Reader | [link](https://www.seeedstudio.com/Grove-125KHz-RFID-Reader.html) | Same RDM6300 chip family — AliExpress generic is ~1/3 the price. |
| Grove Wio-E5 via AliExpress reseller | [link](https://www.aliexpress.com/item/1005007573444408.html) | Identical Seeed module at ~3× the DigiKey/Seeed price. Bought from DigiKey instead. |
