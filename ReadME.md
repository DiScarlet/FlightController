# Custom Flight Controller

A custom STM32F405-based flight controller designed from the ground up for modern FPV drones. Supports 4S–6S LiPo batteries, four ESC outputs with DShot, USB-C programming, and the ICM-42688-P IMU. The repository includes complete schematics, PCB design, CAD assembly, hardware documentation, and firmware flashing/bring-up guides. Designed for Betaflight compatibility with future ArduPilot support and additional onboard peripherals.

A preview of the complete assembly by Autodesk Viewer: https://autode.sk/4bVkogq

---

# A Note to the Reviewer

Dear Reviewer,

Thank you for taking the time to look through my project.

This repository documents the design of my first large hardware project—a custom STM32F405-based flight controller.

Everything here was designed by me from scratch, from selecting the components and drawing the schematic to routing the PCB, creating custom symbols and footprints where needed, writing the documentation, and assembling the CAD model. I deliberately chose not to follow a tutorial or copy an existing flight controller because I wanted to understand how every subsystem actually works. Most of what I learned came from datasheets, reference manuals, application notes, and a lot of trial and error.

This definitely wasn't the fastest way to build a flight controller, but it was the best way for me to learn. There were plenty of mistakes, redesigns, and moments where I questioned my own sanity (especially while routing the buck converter), but every one of them taught me something new.

The development journal intentionally contains both technical notes and my own thoughts throughout the project. I wanted it to show the real engineering process instead of only presenting the finished result.

Unfortunately, manufacturing the PCB, assembling a complete drone, and validating the hardware wasn't realistic within the available time and budget before the Horizons submission deadline. The current demonstration is the completed hardware design, documentation, and the mechanical integration of the flight controller with its intended ESC. I plan to continue the project after Horizons by manufacturing the PCB, adding some more hardware stuff, testing the firmware, and eventually flying it.

---

## Documentation

The repository contains additional documentation describing both the hardware and firmware aspects of the project.

Detailed information about the PCB architecture, power distribution, interfaces, mechanical design, manufacturing considerations, and future hardware revisions can be found in **`Docs/Hardware.md`**.

Firmware-related documentation, including programming interfaces, flashing instructions, hardware bring-up, Betaflight target information, and the planned firmware development roadmap, is available in **`Docs/Firmware.md`**.

---

## Repository Structure

FlightController/
├── CAD_Rendered/             # Fusion 360 assembly and mechanical models
├── FCHardware/               # KiCad project files
├── Devlogs/                  # The overall folder with devlog documents
│   ├── Images/                 # Figures and renders
│   └── Journal.md              # Development journal
├── Docs/                     #Documentation
│   ├── Hardware.md         
│   └── Firmware.md
├── ComponentsReferences.csv  # Component purchasing references (BOM)
├── FCHardware.csv            # Design references and documentation
└── README.md

---

## Gallery

### Schematic Overview

![Schematic](Devlogs/Images/Schematic.png)

### PCB Layout (2D)

![PCB Layout](Devlogs/Images/PCBLayout2D.png)

### PCB Front (3D)

![PCB Front](Devlogs/Images/PCB_Front.png)

### PCB Back (3D)

![PCB Back](Devlogs/Images/PCB_Back.png)

### Fusion 360 Assembly

![Fusion Assembly 1](Devlogs/Images/Fusion_Assembly_1.png)

![Fusion Assembly 2](Devlogs/Images/Fusion_Assembly_2.png)
---

## Acknowledgements

This project would not have been possible without the documentation, manuals, and resources provided by the engineering community. 

Special thanks to:
- STMicroelectronics, TDK InvenSense, Texas Instruments, Diodes Incorporated, Betaflight, Sahil Parashar for providing the generic ESC model that was adapted for this project, KiCad, Autodesk.
- **My family and friends** for their encouragement and support throughout the project.