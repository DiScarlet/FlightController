title: "Flight Controller"
author: "Diana"
description: "It must fly (i'll wrie it later)"
created_at: "2026-07-06"

----------------------
created_at: "2026-07-06"
Lapse Links: 
- https://lapse.hackclub.com/timelapse/7EcZ5cB8u3wI
- https://lapse.hackclub.com/timelapse/V2QrQ_YrS28b
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
- https://lapse.hackclub.com/timelapse/JKiI6UassHQw
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
- https://lapse.hackclub.com/timelapse/zhmaA2kOq_Py
To use more powerful motors, my infrastructure allows me to switch from a 1S to a 2S LiPo battery. This is mainly due to the DRV8833PWP drivers, which accept 2.7V to 10.8V — a span that falls right into the 2S range. To make this work, I chose the TPS62125DSG step-down regulator. I was wondering how to connect the battery to the PCB itself and settled on the Amass XT60PW male PCB-mount connector. Most JST connectors are too weak, and an XT90 is overkill. I ended up a bit confused by all the different power inputs and outputs, but I eventually figured out the wiring and ended up with the following schematic:
![TPS62125DSG Wiring](<Images/Screenshot 2026-07-08 015507.png>)
![ESP32 + Power Schematics](<Images/Screenshot 2026-07-08 015517.png>)

--------------------
created_at: "2026-07-08"
Lapse Links: 
- ss
Changed TPS62125 vs TPS629203 ![alt text](Images/image.png). switching from DRV8833PWP OBSOLETE
This product is no longer in production.
 to DRV8847PWPR custom. switching to 4s lipo.

 Decided with motors to set my setup - https://hobbywinguav.com/product/2807/ XRotor 2807 1300KV https://www.hobbywing.com/uploads/file/20250207/46cccf132a1b9971633a272da27fb76f.pdf
 H bridge to esc
 comopare datasheet of ecs motors
 Xrotor 65A 4in1 Lite BLS RTF esc https://hobbywinguav.com/product/xrotor-65a-4in1-fpv/ 
 https://www.hobbywing.com/en/uploads/file/20250324/715cf619a357b18a11761e3bb13e4f6d.pdf
 custom ESC_Xrotor_65A 4in1![alt text](<Images/Screenshot 2026-07-11 000808.png>)![alt text](<Images/Screenshot 2026-07-11 001029.png>)
 WIRE ESC![alt text](<Images/Screenshot 2026-07-11 002627.png>)
 change conectors to 3 pin for brushless motors