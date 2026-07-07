Custom Flight Controller Project. 
1) As a microcontroller I decided to go with the Adafruit ESP32 Feather V2 https://cdn-learn.adafruit.com/downloads/pdf/adafruit-esp32-feather-v2.pdf
2) Motor Connectors for Conecting to the motors.
3) H - bridge Circuit for controlling the motors.
4) Accelerometer (MPU6050) which also contains a Gyroscope, a temperature sensor and a Digital Motion Processor that act as sensors for the controller's brain.

-----------------
Documentation/Information to read:
L239D - https://www.instructables.com/Using-Motors-With-L293D-IC/ How to control motors.
Nano - https://docs.arduino.cc/learn/electronics/power-pins/ Powering Arduino Nano.
ESP32 - https://www.adafruit.com/product/5900 - Adafruit ESP32 Feather V2
DRV8833 Dual H-Bridge Motor Driver - https://www.ti.com/lit/ds/symlink/drv8833.pdf?ts=1783390141686&ref_url=https%253A%252F%252Fwww.google.com%252F - The datasheet

----------------
Day 1: Initial components added by schematics with ESP32 WROOM Module.
Day 2: Too many unnessary componnets. I chnaged main controler to Feather, reduced the amount of componnets drastically.  