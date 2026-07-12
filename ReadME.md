Custom Flight Controller Project. 
1) As the main microcontroller, I chose the Adafruit ESP32 Feather V2. It provides Wi-Fi, Bluetooth, USB connectivity, and sufficient GPIOs for the flight controller.
https://cdn-learn.adafruit.com/downloads/pdf/adafruit-esp32-feather-v2.pdf
2) A 4-in-1 Hobbywing XRotor 65A ESC is used to drive the 4 brushless motors. The flight controller communicates with the ESC using PWM/DShot signals and receives current and telemetry data.
3) Accelerometer/Gyroscope (MPU6050) provides acceleration, angular velocity, temperature, and Digital Motion Processor (DMP) data for attitude estimation and flight stabilization.
4) 4S to 5V Power Converter: A TPS629203 buck converter steps the 4S LiPo battery voltage down to a regulated 5 V supply for the ESP32 Feather and onboard electronics.
5) Power Monitoring: Battery voltage is monitored using a resistor divider connected to an ESP32 ADC pin, while battery current is monitored through the ESC's analog current output.
-----------------
Documentation / Information:
Adafruit ESP32 Feather V2
https://www.adafruit.com/product/5900
MPU6050 Register Map & Datasheet
https://cdn.sparkfun.com/datasheets/Sensors/Accelerometers/RM-MPU-6000A.pdf
TPS629203 Buck Converter Datasheet
https://www.ti.com/lit/ds/symlink/tps629203.pdf
Hobbywing XRotor 2807 1300KV Motor
https://www.hobbywing.com/uploads/file/20250207/46cccf132a1b9971633a272da27fb76f.pdf
Hobbywing XRotor 65A 4-in-1 Lite BLS V2 ESC
https://www.hobbywing.com/en/uploads/file/20251120/81969c41227e3db78d441e9c20476cf1.pdf

----------------

