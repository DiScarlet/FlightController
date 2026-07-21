# Firmware Guide

This document describes how to flash and configure the custom flight controller.

---

# Requirements

Software

- STM32CubeProgrammer
- Betaflight Configurator
- STM32 USB Driver (Windows)

Hardware

- USB-C cable
- or ST-Link V2 programmer

---

# Flashing via USB DFU

1. Connect BOOT0 to 3.3 V using tweezers or a jumper.
2. Connect the board to the PC using USB-C.
3. Press RESET or reconnect USB.
4. The STM32 should enumerate as **STM32 BOOTLOADER**.

Open STM32CubeProgrammer.

Select:

```
USB
```

Connect to the device.

Open the firmware (.bin or .hex).

Press **Download**.

Disconnect BOOT0.

Reset the board.

---

# Flashing using ST-Link

Connect

| ST-Link | Flight Controller |
|---------|-------------------|
| SWDIO | SWDIO |
| SWCLK | SWCLK |
| GND | GND |
| 3V3 | 3V3 |

Open STM32CubeProgrammer.

Select

```
ST-Link
```

Connect.

Open firmware.

Download.

Reset the board.

---

# First Bring-up Checklist

Verify in order:

- [ ] No excessive current draw
- [ ] 5 V present
- [ ] 3.3 V present
- [ ] STM32 detected
- [ ] USB communication works
- [ ] SPI communication with IMU
- [ ] IMU responds correctly
- [ ] Receiver UART works
- [ ] ESC telemetry works
- [ ] ADC battery voltage works
- [ ] Motor outputs generate DShot

---

# Betaflight Target

This hardware is intended to run a custom Betaflight target.

The target configuration should define:

- SPI IMU
- UART assignments
- Motor outputs
- ADC channels
- LED/Beeper (if implemented)

---

# Future Work

- Create an official Betaflight target
- Add Blackbox support
- Validate ArduPilot compatibility