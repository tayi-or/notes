---
layout: post
category: hardware
tags:
    - raspberry-pi
title: Raspberry Pi Debug Probe Test Point Pinout
---

## Intro
The [Raspberry Pi Debug Probe](https://www.raspberrypi.com/documentation/microcontrollers/debug-probe.html) is a nice little device for interfacing with UART/SWD devices through USB. 
Sure, at £10 it's relatively expensive to the £4 UART probes you can get off Amazon, but those don't come with SWD, a nice little case, or a much nicer cabling situation. (though I wish they included multiple of each, so you could use UART & SWD at the same time, or just leave the cables connected to a device).

## Test Point Pinout

The Debug Probe has a set of test points on the bottom and holes for a 3 pin connector connected to internal points on the board. The problem is they're not documented very well.

![lrg](https://github.com/TayIorRobinson/notes/assets/74316107/081be4cf-1d6a-4c64-809e-b92333ef6fd4)

### 3 pin connector
There's a unsoldered space for a 3 pin connector. From top to bottom, they're connected to:

| Shape  | TP# |
|--------|-----|
| Square | 23  |
| Round  | 24  |
| Round  | 25  |

### Test Points

| TP# | Interface | GPIO |  Description |
|-----|-----------|------|--------------|
|  1  | Power     | GND  | |
|  8  | Power     | GND  | |
|  11 | Power     | GND  | |
|  16 | Power     | GND  | |
|  20 | Power     | GND  | |
|  24 | Power     | GND  | |
|  19 | Power     | VBUS | 5V (from USB) |
|  26 | Power     | IOVDD| 3.3V |
|  27 | Power     | DVDD | 1.1V |
|   2 | USB       | USB_DM | USB Data - |
|   3 | USB       | USB_DP | USB Data + |
|   5 | LED       | GPIO2 | Connected to GPIO2 via 470 resistor (for red power LED) |
|  17 | LED       | GPIO7 | Connected to GPIO7 via 470 resistor (for green `UART_RX` LED) |
|  18 | LED       | GPIO15 | Connected to GPIO15 via 470 resistor (for green `DAP_CONNECTED` LED) |
|  21 | LED       | GPIO8 | Connected to GPIO8 via 470 resistor (for ywllow `UART_TX` LED)  |
|  22 | LED       | GPIO16 | Connected to GPIO16 via 470 resistor (for yellow `DAP_TARGET_CONNECTED` LED) |
|   6 | System    | QSPI_SS | Connected to the BOOTSEL button, in turn, connected to QSPI_SS via 1K resistor (forces the 2040 to boot from USB) |
|  13 | System    | RUN | Reset pin |
|   7 | UART1      | GPIO4 | UART1 TX (connected directly to U connector) |
|   9 | UART1      | GPIO5 | UART1 RX (connected directly to U connector). Connected via `74AUP1T17GW` to GPIO5, connected directly to GPIO6. |
|  10 | SWD        | GPIO10 | SWCLK (connected directly to D connector) |
|  12 | SWD        | GPIO13 | SWDIO (connected directly to D connector) Connected via `74AUP1T17GW` to GPIO13, connected directly to GPIO14. |
|  14 | SWD (probe) | SWDIO | for the debug probe itsself |
|  15 | SWD (probe) | SWCLK | for the debug probe itsself |
|  23 | GPIO      | GPIO0 | |
|  25 | GPIO      | GPIO1 | |
