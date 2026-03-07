## Module's Major Components Selection Process

### Power Management

1. AMS1117-3.3 Linear Voltage Regulator

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/483f524a-cae2-4ca4-99ad-34c2309e0fa7" />


- $0.50 each  
-[link](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4R2/16162643)

| Pros | Cons |
|-----|-----|
| Simple design with minimal external components | Lower efficiency compared to switching regulators |
| Stable 3.3V output for ESP32 | Can generate heat if input voltage is high |
| Low cost and widely available | Limited current compared to switching regulators |

2. TPS62162 Buck Converter

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/af68066c-cdb1-4a87-b838-1a191f027d5d" />



- $1.57 each  
[link](https://www.digikey.com/en/products/detail/umw/AMS1117-3-3/17635254)

| Pros | Cons |
|-----|-----|
| Higher efficiency power conversion | Requires inductor and more components |
| Less heat generation | More complex PCB layout |
| Better for high current systems | Slightly higher cost |

**Choice:** AMS1117-3.3 Linear Voltage Regulator  

**Rationale:** The AMS1117 was selected because it provides a simple and reliable way to generate the 3.3V rail required by the ESP32 module. The design only requires a few external capacitors and keeps the PCB layout simple. For this subsystem the efficiency loss compared to a switching regulator is acceptable.

---

### Microcontroller / WiFi Module

1. ESP32-S3-WROOM-1

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/4152952c-1517-43f5-b598-ac4206570d40" />


- $5.06 each  
-[link](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4R2/16162643)

| Pros | Cons |
|-----|-----|
| Integrated WiFi and Bluetooth | High peak current during WiFi transmission |
| Combines MCU and wireless radio | Requires antenna keep-out region |
| Multiple communication interfaces (UART, SPI, I2C) | Requires stable 3.3V power design |

2. PIC18F57Q43 + External WiFi Module

| Pros | Cons |
|-----|-----|
| Flexible microcontroller architecture | Requires external WiFi module |
| Good for general embedded control | More complex hardware design |
| Large development ecosystem | Larger PCB footprint |

**Choice:** ESP32-S3-WROOM-1  

**Rationale:** The ESP32-S3-WROOM-1 was selected because it integrates the microcontroller and WiFi communication in a single surface mount module. This reduces hardware complexity, saves PCB space, and simplifies firmware development while still providing multiple communication interfaces.
