# Hardware Documentation

## Overview

This document describes the hardware architecture of the custom STM32F405-based flight controller.

The board is designed for 4S–6S FPV drones and follows the standard 30.5 × 30.5 mm flight controller mounting pattern, allowing it to stack directly with compatible 4-in-1 ESCs.

---

# Board Specifications

| Parameter | Value |
|-----------|-------|
| MCU | STM32F405RGT6 |
| IMU | ICM-42688-P |
| Input Voltage | 4S–6S LiPo |
| Regulated Rails | 5 V, 3.3 V |
| Mounting Pattern | 30.5 × 30.5 mm |
| Board Size | 39 × 39 mm |
| Corner Radius | 3.2 mm |
| PCB Layers | 2 |
| PCB Thickness | 1.6 mm |

---

# System Architecture

```
        LiPo Battery
              │
              ▼
      TPSM63603 Buck
         5 V Rail
              │
              ▼
      AP2112K-3.3 LDO
         3.3 V Rail
              │
              ▼
      STM32F405RGT6
       │        │
       │        ├── USB-C
       │
       ├── SPI
       ▼
ICM-42688-P IMU

UART
 ├── ExpressLRS Receiver
 └── ESC Telemetry

ADC
 ├── Battery Voltage
 └── Current Sense

PWM / DShot
 └── ESC
```

---

# Power Distribution

## Battery Input

The flight controller is powered directly from the ESC battery pads.

Supported input voltage:

- 4S LiPo
- 5S LiPo
- 6S LiPo

---

## 5 V Rail

Generated using:

**TPSM63603**

Purpose:

- USB power
- Receiver
- External peripherals
- Input for the 3.3 V LDO

---

## 3.3 V Rail

Generated using:

**AP2112K-3.3**

Powers:

- STM32F405
- ICM-42688-P
- Digital logic

---

# Microcontroller

## STM32F405RGT6

Main responsibilities:

- Flight control
- Sensor acquisition
- Motor control
- USB communication
- Battery monitoring
- Receiver communication

Interfaces used:

| Peripheral | Purpose |
|------------|---------|
| SPI | IMU |
| UART | ExpressLRS |
| UART | ESC Telemetry |
| USB FS | Configuration |
| ADC | Battery Voltage |
| ADC | Current Sense |
| SWD | Programming |

---

# IMU

## ICM-42688-P

Communication:

- SPI

Signals:

- CS
- SCLK
- SDI
- SDO
- INT

The IMU is positioned according to the manufacturer's orientation recommendations and surrounded by local decoupling capacitors to minimize supply noise.

---

# USB

Connector:

USB Type-C

Features:

- USB Full-Speed
- ESD protection
- CC pull-down resistors
- USB bootloader support

---

# Receiver

Supported receiver:

- RadioMaster XR1 Nano
- ExpressLRS

Interface:

UART

---

# ESC Interface

Designed for:

- Hobbywing XRotor 65A 4-in-1 ESC

Signals:

- M1
- M2
- M3
- M4
- ESC Telemetry
- Current Sense
- Battery Voltage

---

# Debug Interface

The board exposes the following programming interface:

| Signal |
|---------|
| SWDIO |
| SWCLK |
| NRST |
| BOOT0 |
| GND |
| 3V3 |

BOOT0 and RESET are intentionally implemented as test pads to reduce PCB area.

---

# Test Points

The PCB exposes SMD test pads for:

- 3V3
- 5V
- GND
- BOOT0
- NRST

These simplify firmware flashing, debugging, and power verification.

---

# PCB Layout

The PCB was routed manually.

Design goals:

- Continuous ground plane
- Short decoupling paths
- Minimized via count
- Clean return current paths
- Differential USB routing
- Short SPI traces
- Power-first placement

---

# Protection

The board includes:

- USB ESD protection
- Input voltage regulation
- Multiple local decoupling capacitors
- Ferrite bead filtering for analog supplies

---

# Planned Improvements (Revision 2)

- Cleaner buck converter routing
- Improved connector placement
- Additional UART breakout
- Dedicated GPS connector
- LiDAR support
- Better ESC integration
- Improved mechanical mounting