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
*Table 2: WiFi Compute Module Selection*

| **Component**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
|<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/2357efa5-4d25-429a-a8c1-f5729d65cfb6" /> <br>ESP32-S3-WROOM-1-N4r<br>$5.06 each<br>[link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639?utm_source=chatgpt.com)                 | \* Integrated WiFi and Bluetooth LE<br>\* 1A output capability provides margin above 0.66A required<br>\* Handles ESP32 WiFi transmit burst current safely <br>\* Reduced heat compared to LDO                                              | \* High peak current during WiFi transmission<br>\* Requires antenna keep-out PCB region<br>\* Requires robust 3.3V power design |

**Rationale:** The ESP32-S3-WROOM-1-N4 was selected because it integrates wireless communication and processing into a single certified surface mount module. This reduces integration risk, minimizes board space, and simplifies firmware compared to using a PIC with an external WiFi radio. It provides sufficient GPIO and communication interfaces for UART, SPI, and I2C subsystem coordination.


### Communication Interface to Telescope Controller
*Table 3: Inter-Subsystem Communication*



| **Component**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
|<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/aeb0d15f-7be6-4e72-be5c-c3d6967dc25d" />> <br>ESP32-S3-WROOM-1 UART Interface<br>$15 each<br>[link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-DEVKITC-1-N8R8/15295894?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gclid=Cj0KCQiA7rDMBhCjARIsAGDBuEAZsZZ5mP-KZ28V1nJSp50fG-HfMVz22OIJQpd5z0FkEwOMi1zYkvkaAnhQEALw_wcB)   | \* No additional hardware required<br>\*Minimal PCB space<br>\* Easy debugging with serial monitory<br>\*Reliable for command and status exchange                                                                                               | \*Lower bandwidth than SPI<br>\* Point-to-point only |

**Rationale:** UART was selected for communication between the WiFi subsystem and the main telescope controller because it minimizes hardware complexity, requires only two signal lines, and supports straightforward debugging during system integration.







-----------















