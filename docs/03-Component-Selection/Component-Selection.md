---
title: Module's Selected Major Components
---

## Module's Selected Major Components

The following sections describe the selected major components necessary for the EV Telescope WiFi subsystem.


### Power Management

*Table 1: 3.3V Regulation – WiFi Subsystem*



| **Component**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
|<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/d44e3daf-0e48-44d9-be83-19947280d66a" /> <br>TPS62162DSGR 3.3V Buck Converter<br>$1.57 each<br>[link to product](https://www.digikey.com/en/products/detail/texas-instruments/TPS62162DSGR/2833447?utm_source=chatgpt.com)                 | \* High efficiency switching regulator<br>\* Fully surface mount compliant with EGR 314<br>\* Multiple UART, SPI, I2C peripherals <br>\* Native USB support  <br>\*  Large ecosystem and documentation support                                          | \* Requires inductor and additional passive components for interface<br>\* Requires careful PCB layout to reduce switching noise |

**Rationale:** The ESP32-S3 WiFi module can draw up to ~330mA during transmit bursts. Designing for 500mA plus a 25 percent safety margin requires at least 0.66A capacity. A 1A buck regulator provides sufficient electrical and thermal headroom while maintaining efficiency. Compared to an LDO, this solution reduces heat and improves rail stability during WiFi activity.



### Microcontroller / WiFi Module

**Table 2: WiFi Compute Module Selection**

| Component | Pros | Cons |
|-----------|------|------|
| <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/e81cb26b-062b-47e2-86ba-59332f8d16fc" /><br>ESP32-S3-WROOM-1-N4R2<br>$5.06 each<br>[link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4R2/16162643?utm_source=chatgpt.com) | * Integrated WiFi and Bluetooth LE<br>* Combines microcontroller and wireless communication in one module<br>* Reduces PCB design complexity<br>* Supports UART, SPI, and I2C communication interfaces<br>* Large development ecosystem | * High peak current during WiFi transmission<br>* Requires antenna keep-out region on PCB<br>* Requires stable 3.3V power supply |

**Rationale:**  
The ESP32-S3-WROOM-1 module was selected as the main controller and wireless communication interface for the subsystem. It integrates processing capability and WiFi connectivity into a single surface-mount module. This reduces system complexity, saves PCB space, and simplifies firmware development while providing multiple communication interfaces for integration with external devices.

### Communication Interface to Telescope Controller
*Table 3: Inter-Subsystem Communication*



### Communication Interface to Telescope Controller

**Table 3: Inter-Subsystem Communication**

| Component | Pros | Cons |
|-----------|------|------|
| <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/b9246716-b9bb-468c-a3e5-59f7d7faf318" /><br>ESP32-S3-WROOM-1 UART Interface<br>Integrated in ESP32 module<br>[link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4R2/16162643) | * No additional hardware required<br>* Minimal PCB space<br>* Easy debugging using serial monitor<br>* Reliable for command and status communication | * Lower bandwidth compared to SPI<br>* Point-to-point communication only |

**Rationale:**  
UART was selected as the communication interface between the ESP32 WiFi subsystem and the telescope controller. The interface requires only two signal lines, TX and RX, which simplifies PCB routing and reduces hardware complexity. UART also allows straightforward debugging and monitoring of system data during development and integration.




-----------















