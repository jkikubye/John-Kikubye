Motion Detection System (ESP32 + PIR + LCD + Blynk)

This project implements a smart motion detection system using an ESP32 board, PIR motion sensor, active buzzer, and a 16x2 I2C LCD display.  
The system also integrates with Blynk IoT, allowing remote monitoring and control from the Blynk mobile app or web dashboard.

Features

- Detects motion using a PIR sensor  
- Displays system status on a 16x2 I2C LCD  
- Activates a buzzer when motion is detected  
- Sends real‑time motion updates to Blynk  
- Allows enabling/disabling the PIR sensor remotely via Blynk  
- Works in Wokwi simulation and on real hardware  

Hardware Components

- ESP32 DevKit V1  
- PIR Motion Sensor (HC‑SR501)  
- Active Buzzer  
- 16x2 LCD with I2C module  
- Jumper wires  
- USB cable  

Wiring Diagram

PIR Sensor → ESP32
PIR Pin to ESP32 Pin 

VCC to 5V 
GND to GND
OUT to GPIO 27 

Buzzer → ESP32
Buzzer Pin to ESP32 Pin 

 + to GPIO 25
 – to GND 

I2C LCD → ESP32
LCD Pin to ESP32 Pin 

VCC to 5V 
GND to GND 
SDA to GPIO 21 
SCL to GPIO 22 

Blynk Setup

Create a new Blynk Template and copy:

- BLYNK_TEMPLATE_ID
- BLYNK_TEMPLATE_NAME
- BLYNK_AUTH_TOKEN

Datastreams
Datastream | Type | Pin 

V0 | Integer | V0 | Enable/Disable PIR 
V1 | String | V1 | Motion Status 

Dashboard Widgets
- Switch → V0 → “Enable Sensor”
- Label → V1 → Display Type: Text

