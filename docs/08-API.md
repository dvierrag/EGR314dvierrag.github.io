# Message API – Telescope System

## Overview
This page defines the UART message API used for communication between subsystems in the telescope project. Each message specifies the structure of the message data field, including byte layout, data types, valid ranges, and examples.

All message data is placed inside the class protocol packet and does not include prefix, suffix, sender, or receiver bytes.

--------------------------------------------------

## Messages Received

### Input Coordinates

Purpose: Receive target X and Y coordinates.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 10
2-3 | x_coord | int16_t | -1000 | 1000 | 120
4-5 | y_coord | int16_t | -1000 | 1000 | -45

Total Bytes: 5

--------------------------------------------------

### Turn On Telescope

Purpose: Enable telescope system.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 12
2 | power_enable | uint8_t | 0 | 1 | 1

Total Bytes: 2

--------------------------------------------------

### Adjust Scope

Purpose: Adjust telescope position incrementally.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 13
2-3 | delta_x | int16_t | -500 | 500 | 15
4-5 | delta_y | int16_t | -500 | 500 | -10

Total Bytes: 5

--------------------------------------------------

### Refresh Data

Purpose: Request periodic data update.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 16
2 | period_lsb | uint8_t | 0 | 255 | 232
3 | period_msb | uint8_t | 0 | 255 | 3

Total Bytes: 3

--------------------------------------------------

## Messages Sent

### WiFi Status

Purpose: Send WiFi connection status.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 11
2 | wifi_connected | uint8_t | 0 | 1 | 1
3 | signal_strength | int8_t | -100 | 0 | -62

Total Bytes: 3

--------------------------------------------------

### Move Scope

Purpose: Command motors to move telescope.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 14
2-3 | motor_x | int16_t | -255 | 255 | 80
4-5 | motor_y | int16_t | -255 | 255 | -60

Total Bytes: 5

--------------------------------------------------

### Data Received Acknowledgement

Purpose: Confirm valid message reception.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 15
2 | received_type | uint8_t | 1 | 255 | 14
3 | status_code | uint8_t | 0 | 255 | 1

Total Bytes: 3

--------------------------------------------------

### Display Data on OLED

Purpose: Send display values.

Byte | Variable Name | Type | Min | Max | Example
1 | message_type | uint8_t | 1 | 255 | 17
2-3 | display_x | int16_t | -1000 | 1000 | 120
4-5 | display_y | int16_t | -1000 | 1000 | -45
6 | status_flags | uint8_t | 0 | 255 | 3

Total Bytes: 6

--------------------------------------------------

## Receive Handling

My receiver processes all incoming UART messages.

- Messages addressed to me are parsed and handled
- Messages for other subsystems are forwarded unchanged
- Messages originating from my own sender are discarded
- Oversized messages are ignored
- Malformed messages are ignored

A valid message triggers an acknowledgement containing:
- message type
- received data

--------------------------------------------------

## Send Handling

My sender constructs valid UART packets.

- Includes correct framing bytes
- Uses valid sender and receiver IDs
- Ensures message size is within limits
- Prevents malformed data

The sender:
- Sends example messages with changing values
- Prioritizes forwarding received messages
- Uses non blocking timing for transmission

--------------------------------------------------

## Testing Notes

- Each message type can be verified through UART output
- Acknowledgements confirm correct parsing
- Invalid messages are ignored without response
- Loop timing ensures periodic updates without blocking

--------------------------------------------------

