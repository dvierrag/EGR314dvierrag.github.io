---
title: Appendix - Controller Table for the ESP32
---

| ESP Info | Answer | Help |
|---------|--------|------|
| Model | ESP32-S3-WROOM-1-N4 | Include the entire part number |
| Product Page URL | [Espressif Product Page](https://www.espressif.com/en/products/modules/esp32-s3-wroom-1) | Found on Espressif.com |
| ESP32-S3-WROOM-1-N4 Datasheet URL | [Module Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-1_datasheet_en.pdf) | Datasheet for module |
| ESP32 S3 Datasheet URL | [ESP32-S3 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf) | Has more detail on functions |
| ESP32 S3 Technical Reference Manual URL | [Technical Reference Manual](https://www.espressif.com/sites/default/files/documentation/esp32-s3_technical_reference_manual_en.pdf) | Details on I/O multiplexing and USB |
| Vendor link | [DigiKey ESP32-S3-WROOM-1-N4](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/) | Vendor purchase link |
| Code Examples | [ESP-IDF GitHub](https://github.com/espressif/esp-idf) | Espressif official framework |
| External Resources URL(s) | [Random Nerd Tutorials ESP32-S3](https://randomnerdtutorials.com/esp32-s3/) | Tutorials and examples |
| Unit cost | ~$5.00 | Approximate price from DigiKey |
| Absolute Maximum Current for entire IC | 500 mA | As found in datasheet |
| Supply Voltage Range | 3.0V – 3.6V (3.3V nominal) | From datasheet |
| Absolute Maximum current (for entire IC) | 500 mA | As found in datasheet |
| Maximum GPIO current (per pin) | 40 mA | Recommended lower in practice |
| Supports External Interrupts? | Yes | GPIO interrupt supported |
| Required Programming Hardware, Cost, URL | USB cable (USB programming built in) | No external programmer needed |


| Module | # Available | Needed | Associated Pins (or * for any) |
|-------|-------------|--------|--------------------------------|
| UART | 3 | 1 | GPIO43 (TX), GPIO44 (RX) |
| external SPI* | 2 | 1 | GPIO10 (CS), GPIO11 (MOSI), GPIO12 (SCLK), GPIO13 (MISO) |
| I2C | 2 | 1 | GPIO8 (SDA), GPIO9 (SCL) |
| GPIO | 45 | 3 | * |
| ADC | 20 channels | 1 | GPIO1 |
| LED PWM | 8 | 1 | GPIO5 |
| Motor PWM | 8 | 1 | GPIO6 |
| USB Programmer | 1 | 1 | GPIO19 (USB D-), GPIO20 (USB D+) |



\* The ESP32-S2 has multiple SPI interfaces, but some are for internal use
