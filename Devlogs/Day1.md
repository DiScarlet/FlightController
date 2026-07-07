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
8) Battery Charger: To prevent damage to the battery.Accelerometer (MPU6050): This also contains a gyroscope, a temperature sensor, and a Digital Motion Processor that act as sensors for the controller's brain.
![Schematics Day 1](<Images/Screenshot 2026-07-07 011820.png>)
This is going to be an epic project, and I am really excited to begin. I am still not sure if this is the right controller to choose, but many tutorials suggest it, so who am I to go against them?
I like what I've done so far. Even though I am still not finished, I understand way more now by looking at tutorials and doing my own thing. I'll try to optimize it tomorrow.