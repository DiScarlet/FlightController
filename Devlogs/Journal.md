title: "Flight Controller"
author: "Diana"
description: "It must fly (i'll wrie it later)"
created_at: "2026-07-06"

----------------------
created_at: "2026-07-06"
Lapse Links: 
- [Lapse 1](https://lapse.hackclub.com/timelapse/7EcZ5cB8u3wI)
- [Lapse 2](https://lapse.hackclub.com/timelapse/V2QrQ_YrS28b)
Day 1: I am really excited to start this amazing project! 
I'll put a lot of work into this. I looked up some tutorials already, but a lot of them are too old and don't use modern technology or they use components I'd prefer not to.I want to start by following the schematics in the tutorial, and then, once I understand the full idea, switch to a completely different version created entirely by me.
I added the initial component schematics with the ESP32 WROOM Module. I might change it later, but it is currently missing a lot of components, so the tutorial has to add them and wire them up. This will help me better understand the internal structure of the ESP32 WROOM module. Even if I switch to more modern microcontrollers later, it will still help me progress faster because I will understand the internal wiring.
So, here is the basic structure of all the components that I've added and wired:
1) Microcontroller: I decided to go with the ESP32 WROOM 32.
2) CP2104: For USB-to-UART communication.
3) Flashing Sequence: For automatic firmware updates.
4) USB-B / USB-C: I will decide on one later. 
5) Motor Connectors: For connecting to the motors.
6) H-Bridge Circuit: For controlling the motors.
7) 3V3 Voltage Regulator: For stabilizing the input voltage to the ESP32.
8) Battery Charger: To prevent damage to the battery.
9) Accelerometer (MPU6050): This also contains a gyroscope, a temperature sensor, and a Digital Motion Processor that act as sensors for the controller's brain.
![Schematics Day 1](<Images/Screenshot 2026-07-07 011820.png>)
This is going to be an epic project, and I am really excited to begin. I am still not sure if this is the right controller to choose, but many tutorials suggest it, so who am I to go against them?
I like what I've done so far. Even though I am still not finished, I understand way more now by looking at tutorials and doing my own thing. I'll try to optimize it tomorrow.

---------------------
created_at: "2026-07-07"
Lapse Links: 
- [Lapse 3](https://lapse.hackclub.com/timelapse/JKiI6UassHQw)
Day 2: Even though I really enjoyed the progress of working on a lot of interesting stuff yesterday, there were too many unnecessary components. I changed the main controller to the Adafruit ESP32 Feather V2, which reduced the amount of components drastically.
This board has a lot of components already integrated into its internal structure, so I could alter the following elements:
1) Microcontroller: Adafruit ESP32 Feather V2. Why V2? It has USB-C and easier power management already integrated.
2) Removed CP2104: Already integrated into item 1. 
3) Removed Flashing Sequence: Already integrated into item 1.
4) Removed USB-B / USB-C: Already integrated into item 1.
5) H-Bridge Circuit: Upgraded to more modern DRV8833PWP drivers.
6) Removed 3V3 Voltage Regulator: Already integrated into item 1. 
7) Removed Battery Charger: Already integrated into item 1. 

![Schematics Day 2](<Images/Screenshot 2026-07-07 222645.png>)
Overall, the schematics look way more readable now, and the component switch was well worth the trouble. It did not take me that long, but it will definitely make assembly way easier.

--------------------
created_at: "2026-07-08"
Lapse Links: 
- [Lapse 4](https://lapse.hackclub.com/timelapse/zhmaA2kOq_Py)
To use more powerful motors, my infrastructure allows me to switch from a 1S to a 2S LiPo battery. This is mainly due to the DRV8833PWP drivers, which accept 2.7V to 10.8V — a span that falls right into the 2S range. To make this work, I chose the TPS62125DSG step-down regulator. I was wondering how to connect the battery to the PCB itself and settled on the Amass XT60PW male PCB-mount connector. Most JST connectors are too weak, and an XT90 is overkill. I ended up a bit confused by all the different power inputs and outputs, but I eventually figured out the wiring and ended up with the following schematic:
![TPS62125DSG Wiring](<Images/Screenshot 2026-07-08 015507.png>)
![ESP32 + Power Schematics](<Images/Screenshot 2026-07-08 015517.png>)

--------------------
created_at: "2026-07-11"
Lapse Links: 
- [Lapse 5](https://lapse.hackclub.com/timelapse/zi6OlWzVVC0I)
Today I made significant modifications to the flight controller design. I stepped up from a simple 2S brushed drone concept to the prototype architecture of a real 4S 7" brushless drone.

1. Updated the buck converter

I replaced the TPS62125 with the newer TPS629203, which supports my new power requirements and offers better efficiency.![TPS629203](Images/image.png) 


2. Switched from brushed to brushless architecture

Initially, I considered replacing the DRV8833PWP because it is obsolete with the DRV8847PWPR. However, since I had to redesign the motor-driving stage anyway, I decided it made more sense to switch to brushless motors and use a dedicated 4-in-1 ESC instead of H-bridges.

Because the TPS629203 supports a 4S LiPo, I also upgraded the battery from 2S to 4S. This removed the need for additional power circuitry changes and resulted in a much cleaner flight controller schematic.

3. Selected the propulsion system

To avoid designing around unknown components, I chose the motors first and built the rest of the system around them.

Motor: Hobbywing XRotor 2807 1300KV

Product:
https://hobbywinguav.com/product/2807/

Datasheet:
https://www.hobbywing.com/uploads/file/20250207/46cccf132a1b9971633a272da27fb76f.pdf


4. Selected the ESC

Since I switched to brushless motors, I removed the H-bridge motor drivers and replaced them with a 4-in-1 ESC.

After comparing several candidates and checking compatibility with the selected motors, I chose the:

Hobbywing XRotor 65A 4-in-1 Lite BLS V2 ESC

Datasheet:
https://www.hobbywing.com/en/uploads/file/20251120/81969c41227e3db78d441e9c20476cf1.pdf

Product:
https://www.drone-fpv-racer.com/en/hobbywing-65a-4in1-6s-lite-bls-v2-fpv-esc-15678.html
[BLS Version](<Images/Screenshot 2026-07-11 032116.png>)

5. Updated motor connections

I initially changed the motor connectors to 3-pin connectors for brushless motors.

Later, I realised that since the motors connect directly to the ESC, the flight controller PCB does not need motor connectors. Therefore, I removed them from the schematic.

6. Added battery monitoring

I added:

Battery voltage monitoring using a resistor divider connected to an ESP32 ADC pin.
Battery current monitoring using the ESC's analog current output connected to another ESP32 ADC pin.
ESC telemetry connected to a UART RX pin on the ESP32.
 
 
7. Updated the power architecture

The battery is now connected directly to the ESC through an XT60 connector.

I also added:

a 680 µF bulk capacitor (provided with the ESC),
a TVS diode across VBAT and GND for transient protection.

TODO:
- Replace the ESP32 Feather development board with a custom ESP32 circuit in the final design.
- Verify the ESC telemetry connector (SH1.0) and determine the best way to interface it with my PCB.
- Verify that the ESC current output is 3.3 V compatible before connecting it directly to the ESP32 ADC.
- Run KiCad ERC and begin PCB layout.

![Full Shcematics of Today](<Images/Screenshot 2026-07-11 031332.png>)