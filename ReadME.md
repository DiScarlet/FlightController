Custom Flight Controller Project. 
1) The flight controller is based on the ESP32-S3-WROOM-1U module.
2) A 4-in-1 Hobbywing XRotor 65A ESC is used to drive the 4 brushless motors. The flight controller communicates with the ESC using PWM/DShot signals and receives current and telemetry data.
3) Accelerometer/Gyroscope (MPU6050) provides acceleration, angular velocity, temperature, and Digital Motion Processor (DMP) data for attitude estimation and flight stabilization.
4) 4S to 5V Power Converter: A TPS629203 buck converter steps the 4S LiPo battery voltage down to a regulated 5 V supply for the ESP32 Feather and onboard electronics.
5) Power Monitoring: Battery voltage is monitored using a resistor divider connected to an ESP32 ADC pin, while battery current is monitored through the ESC's analog current output.
6) The controller is designed around Hobbywing XRotor 2807 1300KV brushless motors.
-----------------
Documentation / Information:
ESP32-S3-WROOM-1U Datasheet
https://documentation.espressif.com/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf
MPU6050 Register Map & Datasheet
https://cdn.sparkfun.com/datasheets/Sensors/Accelerometers/RM-MPU-6000A.pdf
TPSM63603 Buck Converter Datasheet
https://www.ti.com/lit/ds/symlink/tpsm63603.pdf
Hobbywing XRotor 2807 1300KV Motor
https://www.hobbywing.com/uploads/file/20250207/46cccf132a1b9971633a272da27fb76f.pdf
Hobbywing XRotor 65A 4-in-1 Lite BLS V2 ESC
https://www.hobbywing.com/en/uploads/file/20251120/81969c41227e3db78d441e9c20476cf1.pdf

----------------

