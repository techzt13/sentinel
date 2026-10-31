# Setup Guide

## Stage 1 — Prepare the SD card

1. Format the microSD card as **FAT32** (8–16 GB, SDHC).
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

## Stage 4 — Attach the Cap (NFC + Sub-GHz)

1. Power off. Press the Cap onto the ADV's top header. Screw on the antenna (finger-tight).
2. Insert SD, power on, boot **Bruce**.
3. **Config → RF / RFID module** → select the Cap (CC1101 + ST25R NFC).
   - Known bug (Bruce 1.16.x): CC1101 pin selection may reset on reboot — re-select in Config; NFC settings persist.
4. Test NFC: RFID/NFC menu → **Read tag** on my own blank tag or Octopus card (FeliCa, read-only UID).
5. Test Sub-GHz: RF menu → **Scan/Copy** on my own 433 MHz remote.

## Stage 5 — Safe first tests

1. **WiFi scan** of my own network (Evil-M5Project).
2. **Captive portal** on my own test SSID; connect with my own phone.
3. **NFC** read → write → emulate my own tags.
4. **IR** blast on my own TV.
5. **Sub-GHz** capture/replay my own remote.
6. **Handshake capture** on my own router, then crack my own password.
