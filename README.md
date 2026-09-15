# Pico Ducky
<img width="2160" height="906" alt="3D_PCB1_2026-09-15" src="https://github.com/user-attachments/assets/4c0e68f7-5f56-40d7-ade1-88d2892c2dce" />


A compact, open-source RP2040-based board (schematic name: **RP DUCKY**, board name: **PI-Ducky**) designed to run HID-scripting firmware such as [Pico-Ducky](https://github.com/dbisu/pico-ducky) or CircuitPython-based keystroke automation tools. Built entirely around the Raspberry Pi RP2040 microcontroller with onboard QSPI flash, USB, and user-accessible buttons.

## Overview

This board is a minimal RP2040 reference design, similar in spirit to a Raspberry Pi Pico, but tailored with extra buttons for interactive projects and USB HID scripting use cases.

## Hardware Features

- MCU: Raspberry Pi **RP2040** (QFN-56)
- Flash: Winbond **W25Q128JVSIQ**, 16 MB QSPI NOR flash
- Crystal: 12 MHz crystal (U2) with 15 pF load capacitors
- USB: USB 2.0 full-speed, D+/D- with 27.4 Ω series termination resistors (R1, R2)
- Power: 3.3 V (3V3) and 1.1 V (1V1) core rails, fed from USB VBUS through a linear regulator
- Buttons: 3× tactile switches — SW1 (RUN/Reset), SW2 and SW3 (user buttons)
- Debug: SWCLK / SWD test points broken out for programming/debugging
- Decoupling: Multiple 100 nF ceramic capacitors across IOVDD/DVDD/USB_VDD rails, plus 10 µF bulk caps (C1, C15, C16)

## Pinout Summary (RP2040)

- **GPIO0–GPIO29**: General purpose I/O, broken out from the RP2040
- **QSPI_SS / QSPI_SD0-3 / QSPI_SCLK**: Dedicated QSPI bus to the onboard W25Q128 flash (also broken out to header pins for external use/switches SW2/SW3)
- **USB_DP / USB_DM**: USB data lines, through 27.4 Ω series resistors
- **RUN**: Reset line, pulled via SW1
- **SWCLK / SWD**: SWD debug interface
- **TESTEN**: Tied per RP2040 reference design
- **VREG_IN / VREG_VOUT**: Onboard 1.1 V regulator input/output for the RP2040 core

## Power

- USB VBUS feeds the onboard voltage regulator, producing the 3.3 V (3V3) rail.
- The RP2040's internal switching regulator (VREG) steps 3V3 down to 1.1 V (1V1) for the DVDD core rail.
- Each IOVDD/DVDD/USB_VDD pin group is individually decoupled with 100 nF capacitors close to the package, following the standard RP2040 layout guidelines.

## Notes

- This design closely follows Raspberry Pi's official RP2040 hardware design guidelines (decoupling, crystal load capacitance, USB termination, flash wiring).
- Intended for hobbyist and educational USB-HID scripting projects. Always use responsibly and only on devices you own or have explicit authorization to test.

## License

MIT
