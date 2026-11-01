# Setup Guide

## Stage 1 — Prepare the SD card

1. Format the microSD card as **FAT32** (16 GB, SDHC).
2. Download the Evil-M5Project repo: https://github.com/7h30th3r0n3/Evil-M5Project (Code → Download ZIP).
3. Copy the SD-card folder contents into a folder named **`evil`** at the SD card root → `SD:/evil/...` (mandatory: startup images and captive-portal sites live there).

## Stage 2 — Flash M5Launcher

1. Desktop **Chrome or Edge** only (Web Serial).
2. Open the M5Launcher web flasher.
3. Plug in the Cardputer via USB-C → Connect/Install → pick the serial port → flash M5Launcher.
4. It boots into a launcher menu that scans the SD card for `.bin` firmware files.

## Stage 3 — Add firmwares to the SD card

1. Download the **Evil-Cardputer** `.bin` (Evil-Flasher page or repo release).
2. Download the latest **Bruce** release for Cardputer.
3. Copy both `.bin` files to the SD card.
4. Insert SD, power on, pick a firmware in M5Launcher. Switchable on every boot.

### Optional: compile Evil-M5Project yourself

1. Arduino IDE + M5Stack board defs (ESP32 **2.1.4 or below** — 3.x alphas break the build).
2. Libraries: `Adafruit_NeoPixel`, `ArduinoJson`, `ESPping`, `IniFile`, `M5GFX`, `M5Unified`, `TinyGPSPlus`, `esp8266audio`.
3. Open `Evil-Cardputer-v1-5-4.ino`.
4. Flash Size **8MB**, Partition Scheme **8M with spiffs (3MB APP/1.5MB SPIFFS)**.
5. Baud `115200`, **PSRAM disabled**.
6. Run the script in `utilities/deauth_prerequisites` (required for deauth).
7. Compile & upload, or:

```bash
arduino-cli core install m5stack:esp32
arduino-cli compile --fqbn m5stack:esp32:m5stack_cardputer \
  --build-property "build.partitions=huge_app" \
  --build-property "upload.maximum_size=3145728" \
  Evil-Cardputer-v1-5-4.ino
arduino-cli upload --fqbn m5stack:esp32:m5stack_cardputer --port COMXX \
  Evil-Cardputer-v1-5-4.ino
```

## Stage 4 — Attach the Hydra (Sub-GHz + 2.4 GHz) and PN532 (NFC)

### Hydra RF 424

1. Power the Cardputer ADV off.
2. Mount the Hydra onto the ADV's top header per Pingequa's instructions; screw on the antenna(s) finger-tight.
3. Insert the SD card, power on, boot **Bruce**.
4. In Bruce, open **Config → RF module** and select the CC1101 (and NRF24 for 2.4 GHz features). If a selection doesn't persist after reboot, re-select it in Config.
5. Test Sub-GHz: RF menu → **Scan/Copy** — capture a signal from your own 433 MHz remote.

### PN532 (NFC)

1. On the PN532 board, set the **DIP switches to I2C mode** (check the silkscreen).
2. Power off. Connect the PN532 to the Cardputer's Grove port with a Grove cable:

   | Grove wire | PN532 pin |
   | --- | --- |
   | Red (5V) | VCC |
   | Black (GND) | GND |
   | Yellow (SDA) | SDA |
   | White (SCL) | SCL |

3. Boot **Bruce** → **Config → RFID module** → select PN532.
4. Test: RFID/NFC menu → **Read tag** on your own blank tag or your own Octopus card (FeliCa, read-only UID check).
5. If nothing is detected: re-check DIP switches and SDA/SCL order — those cause nearly all failures.

### Configuration note (pin budget)

- **RF/NFC session:** Hydra mounted + PN532 on Grove. If Bruce misbehaves with both attached (shared Grove pins), unplug the PN532 while using the Hydra — nothing is soldered.
- **Wardriving session:** remove the Hydra, connect the GPS unit (EXT header G13/G15 per the wardriving firmware's docs). Wardriving is pure WiFi/BLE + GPS — the Hydra contributes nothing there.

## Stage 5 — Safe first tests

1. **WiFi:** set up a spare router (or your own router) as the target. Run Scan WiFi → Select Network in Evil-M5Project against *your own* network only.
2. **Captive portal:** start the portal on your own test SSID and connect with your own phone to see the flow.
3. **NFC:** read, then write, then emulate your own blank NTAG215/MIFARE tags in Bruce.
4. **IR:** try the TV-B-Gone-style IR blast on your own TV.
5. **Sub-GHz:** capture and replay *your own* remote (e.g., a cheap 433 MHz outlet remote bought for this purpose).
6. **Handshake capture** on my own router, then crack my own password.
