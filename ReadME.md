# Custom Flight Controller Project

This project documents the design and development of a custom STM32-based flight controller for 4S–6S FPV drones. The primary goal is to build a fully functional Betaflight-compatible* flight controller from scratch. The hardware is also designed with future ArduPilot compatibility in mind.

## Hardware Overview

1. **Microcontroller:** STM32F405RGT6 (ARM Cortex-M4 @ 168 MHz), selected for native Betaflight support and sufficient resources for future expansion.

2. **Electronic Speed Controller:** Hobbywing XRotor 65A 4-in-1 ESC. The flight controller communicates with the ESC using DShot digital protocol and receives current sensing and ESC telemetry.

3. **Inertial Measurement Unit (IMU):** TDK InvenSense ICM-42688-P connected over SPI for low latency and high update rates required by modern flight control firmware.

4. **Power System:**
   - TPSM63603 synchronous buck converter generates a regulated **5 V** rail from the 4S–6S LiPo battery.
   - AP2112K-3.3 LDO generates a clean **3.3 V** supply for the MCU, IMU, and other sensitive digital electronics.

5. **Power Monitoring:** Battery voltage is measured using a resistor divider connected to an STM32 ADC channel, while battery current is measured using the ESC's analog current output.

6. **Radio Receiver:** ExpressLRS support through the RadioMaster XR1 Nano receiver connected via UART.

7. **Programming & Debugging:**
   - USB Type-C interface for firmware flashing and configuration.
   - SWD programming interface exposed through test pads.
   - BOOT0 and NRST are accessible via test pads instead of physical buttons to reduce PCB size.

8. **Expansion:** Additional UART and I²C interfaces are reserved for future peripherals such as GPS, barometer, LiDAR, FPV camera, VTX control, or other sensors.

9. **Target Platform:** Designed primarily for Betaflight, with hardware compatibility intended for future ArduPilot development.

---

## Documentation / Datasheets

### Microcontroller
- STM32F405xx Datasheet  
  https://www.st.com/resource/en/datasheet/dm00037051.pdf

### IMU
- ICM-42688-P Datasheet  
  https://product.tdk.com/system/files/dam/doc/product/sensor/mortion-inertial/imu/data_sheet/ds-000347-icm-42688-p-v1.6.pdf

### Power
- TPSM63603 Buck Converter  
  https://www.ti.com/lit/ds/symlink/tpsm63603.pdf

- AP2112K-3.3 LDO  
  https://www.mouser.fi/datasheet/3/175/1/AP2112.pdf

### ESC
- Hobbywing XRotor 65A 4-in-1 ESC  
  https://www.hobbywing.com/en/uploads/file/20251120/81969c41227e3db78d441e9c20476cf1.pdf

### Motors
- Hobbywing XRotor 2807 1300KV Motor  
  https://www.hobbywing.com/uploads/file/20250207/46cccf132a1b9971633a272da27fb76f.pdf

### Radio Receiver
- RadioMaster XR1 Nano ExpressLRS Receiver  
  https://radiomasterrc.com/products/xr1-nano-multi-frequency-expresslrs-receiver?variant=46486320480448