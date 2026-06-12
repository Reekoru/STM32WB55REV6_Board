# STM32WB55REV6 Custom Development Board

A compact, custom-designed development board for the **STM32WB55REV6** dual-core Bluetooth Low Energy (BLE) and Zigbee microcontroller. Designed in KiCad, this board features a modern USB-C interface for power/data, a dedicated UART interface for debugging, and a space-saving Tag-Connect TC2030 footprint for SWD programming.

## Features

* **MCU:** STM32WB55REV6 (Dual-core Arm® Cortex®-M4 @ 64 MHz with FPU, Cortex-M0+ @ 32 MHz for network/radio).
* **Connectivity:** On-board RF circuitry and antenna for 2.4 GHz BLE 5.4, Zigbee, and Thread.
* **Power:** USB-C connector with TPS78233DDC 3.3V regulator supplying up to 150 mA.
* **Programming/Debugging:** SWD via a headless **Tag-Connect TC2030** footprint (no-legs/legged variant).
* **Serial Communication:** Dedicated UART breakout header for easy terminal debugging.
* **Peripherals:** 
    * 1x User LED (connected to Pin `PB9`)
    * USB-UART (connected to Pin `PA9` [TX], Pin `PA10` [RX])
    * 1x Reset Button, 1x Boot Button
    * External 32.768 kHz LSE Crystal, 32 MHz HSE Crystal

---

## Hardware Overview

### Pinout Configuration

| Interface | Pin Name | STM32WB55 Pin | Description |
| :--- | :--- | :--- | :--- |
| **UART** | TX / RX | PA9 / PA10 | Debug Serial Port |
| **SWD** | SWO / SWDIO / SWCLK | PB3 / PA13 / PA14 | Tag-Connect TC2030 Programming |
| **User LED** | LED1 | PB9 | Active [High/Low] indicator |

### Power Supply
The board is powered via the **USB-C** connector. The input 5V is regulated down to 3.3V for the MCU and RF front end. 
* **Maximum input voltage:** 5.5V
* **Operating voltage:** 3.3V

---

## Programming and Debugging

### Required Hardware
To flash and debug this board, you will need:
1.  An ST-LINK V2, V3, or a Segger J-Link debugger.
2.  A **Tag-Connect TC2030-IDC** (or TC2030-IDC-NL) cable along with the corresponding retaining clip if using the no-legs version.

### SWD Pinout (TC2030 Footprint)
The Tag-Connect footprint maps to the following standard SWD layout:
* Pin 1: VCC (3.3V)
* Pin 2: SWDIO
* Pin 3: NRST (Reset)
* Pin 4: SWCLK
* Pin 5: GND
* Pin 6: SWO (Optional trace capture)

### Flashing via STM32CubeProgrammer
1. Connect the TC2030 cable to the board and your ST-LINK debugger.
2. Open **STM32CubeProgrammer**, select **ST-LINK** as the interface, and click **Connect**.
3. Browse for your compiled binary/hex file and click **Start Programming**.

---