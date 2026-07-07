Day 2: Even though I really enjoyed the progress of working on a lot of interesting stuff yesterday, there were too many unnecessary components. I changed the main controller to the Adafruit ESP32 Feather V2, which reduced the amount of components drastically.
This board has a lot of components already integrated into its internal structure, so I could alter the following elements:
1) Microcontroller: Adafruit ESP32 Feather V2. (Why V2? It has USB-C and easier power management already integrated.
2) Removed CP2104: Already integrated into item 1. 
3) Removed Flashing Sequence: Already integrated into item 1.
4) Removed USB-B / USB-C: Already integrated into item 1.
5) H-Bridge Circuit: Upgraded to more modern DRV8833PWP drivers.
6) Removed 3V3 Voltage Regulator: Already integrated into item 1. 
7) Removed Battery Charger: Already integrated into item 1. 

![Schematics Day 2](<Images/Screenshot 2026-07-07 222645.png>)
Overall, the schematics look way more readable now, and the component switch was well worth the trouble. It did not take me that long, but it will definitely make assembly way easier.