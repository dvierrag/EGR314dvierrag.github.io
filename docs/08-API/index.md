# Message API – Telescope System

## Overview
This page defines the UART message API used for communication between subsystems. Each message follows the team-defined protocol and includes byte layout, data types, and descriptions.

---

## Message Type Definitions

| Message Type (uint16_t) | Description |
|------------------------|------------|
| 1 | WiFi Signal Received |
| 2 | Set Data Receiver Type (Web or In-person) |
| 3 | Print User Input |
| 4 | Translate Coordinate Input to Motor Input |
| 6 | Power Button Pushed |
| 7 | Set Motor X, Y |
| 8 | Set Roshan subsystem On/Off |

---

## Message Type 1 – WiFi Signal Received

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 1 |
| 3    | wifi         | uint8_t  | boolean WiFi status |

---

## Message Type 2 – Set Data Receiver

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 2 |
| 3-58 | data_string  | char[]   | receiver type string |

---

## Message Type 3 – Print User Input

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 3 |
| 3-58 | input_string | char[]   | user input string |

---

## Message Type 4 – Translate Coordinates

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 4 |
| 3    | x_value      | uint8_t  | X coordinate |
| 4-5  | y_value      | uint16_t | Y coordinate |

---

## Message Type 5 – (If Used in System)

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 5 |
| 3    | x_value      | uint8_t  | X coordinate |
| 4-5  | y_value      | uint16_t | Y coordinate |

---

## Message Type 6 – Power Button

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 6 |
| 3    | button       | uint8_t  | boolean button state |

---

## Message Type 7 – Set Motor X, Y

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 7 |
| 3    | x_value      | uint8_t  | motor X |
| 4-5  | y_value      | uint16_t | motor Y |

---

## Message Type 8 – Subsystem Control

| Byte | Variable Name | Type | Description |
|------|--------------|------|------------|
| 1-2  | message_type | uint16_t | 8 |
| 3    | subsystemState | uint8_t | boolean on or off |

---

## Receive Handling

- Processes messages addressed to this subsystem  
- Forwards messages not intended for this subsystem  
- Discards messages originating from itself  
- Ignores malformed messages  
- Ignores oversized messages  

Valid messages trigger an acknowledgement response.

---

## Send Handling

- Constructs valid UART packets  
- Uses correct message formatting  
- Prevents invalid data sizes  
- Sends example messages for testing  
- Prioritizes forwarding over sending  

---

## Notes

- All message types follow team-defined structure  
- Data must stay within defined byte ranges  
- Message formatting must comply with class protocol  
