---
title: Module's Block Diagram
tags:
- tag1
- tag2
---

## Overview
This block diagram shows the overall system architecture for the WiFi subsystem. Power enters the system through a barrel jack and is regulated to 3.3 V for the ESP32 Wroom module. The ESP32 serves as the main controller and manages communication using WiFi and MQTT. The diagram also shows upstream and downstream connections used to communicate with other team components. This diagram provides a high level understanding of how the power system, controller, and communication interfaces interact within the design.



To get some initial formatting help, one can view ["here"](https://embedded-systems-design.github.io/EGR304DataSheetTemplate/Appendix/basic-markdown-examples/) some basic techniques.


## Example Block Diagram 
Showing an example of how to import a screenshot of the block diagram created outside of git and brought into a page.


<img width="682" height="652" alt="Block Diagram drawio" src="https://github.com/user-attachments/assets/b4e46c29-78bd-4bb9-a72a-017da6f5ca23" />




## Decision Making Process

This WiFi subsystem is simple, reliable and easy to interface with other boards. It uses an ESP32 Wroom to connect to WiFi and then handle messages in the form of MQTT messages sent between the connected boards to update statuses. Power for the PCB is fed through the barrel jack on the bottom right and follows the main power rail down to the PCB edge where it passes through a 3.3 V regulator to safely supply power to the ESP32.

This block diagram details how all of the different features of the PCB meet the product requirements. The Power section shows how the PCB is powered as well as how it connects to other boards on the field. The Communication section shows how the WiFi subsystem is able to communicate with the rest of the team as well as with Dylan and Quinn's boards. The Board Connections section detail the decoupling capacitors and 3.3 V power supply required for the board. Overall, the PCB meets the requirement for reliable wireless communication in a highly organized and testable manner.
