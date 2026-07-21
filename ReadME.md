# Custom Flight Controller

> **Fly Fast. Land Hard. Send It Anyway**

A custom STM32F405-based flight controller designed from the ground up for modern FPV drones. The project covers the complete hardware development process—from schematic capture and PCB layout to mechanical integration and 3D CAD assembly.

The primary goal is to create a fully functional **Betaflight-compatible** flight controller while keeping the hardware flexible enough for future **ArduPilot** support and additional onboard peripherals.

# A Note to the Reviewer

Dear Reviewer,

This project represents my first large-scale PCB design created entirely in KiCad.

Everything you see in this repository—from the schematic and component selection to the PCB layout, routing, design rules, mechanical integration, and documentation—was developed from scratch. I did not follow a tutorial or replicate an existing flight controller design. Instead, I relied primarily on component datasheets, manufacturer reference documentation, application notes, and publicly available hardware documentation to understand how each subsystem should be designed.

I understand that this approach required significantly more time than following an existing design, but that was an intentional decision. Working through the design myself forced me to understand not only *what* needed to be done, but *why*. Every mistake, redesign, and challenge became an opportunity to learn something new, and I believe that experience has been far more valuable than simply reproducing someone else's work.

Like any real engineering project, the repository documents mistakes, redesigns, and the reasoning behind many design decisions. I intentionally logged my personal opinions on what is going on in the development journal rather than only presenting the bare facts because I believe the engineering process is just as valuable as the finished PCB.

---

## Repository Structure

```text
FlightController/
├── CAD_Rendered/             # Fusion 360 assembly and mechanical models
├── FCHardware/               # KiCad project files           
├── Devlogs/
    ├── Images/               # Figures and renders
    └── Journal.md            # Journal / Devlogs
├── Docs/
│   ├── Hardware.md
│   └── Firmware.md
├── ComponentsReferences.csv  # Real parts' links to buy in Finland. Basically, Bill of Materials.
├── FCHardware.csv            # Some documentation links
└── README.md
```

---

## Documentation

The repository contains additional documentation describing both the hardware and firmware aspects of the project.

Detailed information about the PCB architecture, power distribution, interfaces, mechanical design, manufacturing considerations, and future hardware revisions can be found in **`Docs/Hardware.md`**.

Firmware-related documentation, including programming interfaces, flashing instructions, hardware bring-up, Betaflight target information, and the planned firmware development roadmap, is available in **`Docs/Firmware.md`**.


---

## Gallery

### Schematic Overview

![Schematic](<Devlogs/Images/Screenshot 2026-07-21 055718.png>)

### PCB Layout (2D)

![PCB Layout](<Devlogs/Images/Screenshot 2026-07-21 055326.png>)

### PCB Front (3D)

![PCB Front](<Devlogs/Images/Screenshot 2026-07-21 055415.png>)

### PCB Back (3D)

![PCB Back](<Devlogs/Images/Screenshot 2026-07-21 055505.png>)

### Fusion 360 Assembly

![Fusion Assembly 1](<Devlogs/Images/Screenshot 2026-07-21 081357.png>)

![Fusion Assembly 2](<Devlogs/Images/Screenshot 2026-07-21 081416.png>)

---

## Acknowledgements

This project would not have been possible without the excellent documentation, reference manuals, and open-source resources provided by the engineering community. I would like to thank the manufacturers and developers whose work made this project possible.

Special thanks to:

- **STMicroelectronics** for the STM32 documentation.
- **TDK InvenSense** for the ICM-42688-P documentation.
- **Texas Instruments** and **Diodes Incorporated** for detailed power management documentation.
- **Betaflight** for developing an open-source flight control firmware.
- **Sahil Parashar** for sharing the generic model of the ESC which was later modified to represent the ESC used for this project.
- **KiCad** for providing so many opportunities open-sourced.
- **Autodesk** for Fusion 360.
- **Family and Firends** for emotional support.

---

*"Fly Fast. Land Hard. Send It Anyway"*