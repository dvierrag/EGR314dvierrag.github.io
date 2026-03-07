---
title: Module Schematic
---

## Overview

This schematic was designed to support a WiFi enabled embedded system using the ESP32 S3 WROOM 1 module as the main controller. The ESP32 manages communication and processing while providing GPIO connections to external devices through the header connector. Power is supplied through a barrel jack and protected by a fuse before being regulated to 3.3 V using the AMS1117 voltage regulator. Decoupling capacitors are included to stabilize the power rail and reduce electrical noise. The design provides a simple interface for power delivery, signal access, and wireless communication while maintaining proper grounding and power filtering for reliable operation.


<img width="2224" height="1515" alt="image" src="https://github.com/user-attachments/assets/7e3183c4-1518-436c-a4ce-cbc92a57d4d7" />



**Figure 1:** Schematic of the embedded system showing the ESP32 S3 WROOM 1 microcontroller, power regulation circuitry, and external connector interface used to distribute signals and power.

<img width="1503" height="1459" alt="image" src="https://github.com/user-attachments/assets/c46af999-d95f-41a1-acd8-d4668fef0399" />

**Figure 2:** Final PCB layout generated in KiCad showing component placement, routed traces, ground copper zones, and the antenna keep out region for the ESP32 module.

## Resouces

The schematic as a PDF download is available [*here*](https://github.com/user-attachments/files/25808715/EV.scope.pdf), and the Zip folder of the project or for the PCB [*here*](https://github.com/user-attachments/files/25811397/Dylan304.zip).
