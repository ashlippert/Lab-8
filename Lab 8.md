# Lab 8: There's an App for That - App Development

**Authors:**

Ashlyn Lippert and Seth Daniel

**Date:**

March 30th, 2025

## Introduction
   The purpose of this lab is to explore mobile app development by creating a simple remote control app for a SparkFun robot car using the MIT App Inventor platform. This lab introduces the process of developing an Android app to communicate wirelessly with the robot via Bluetooth, replacing the need for physical USB connections. Bluetooth technology, widely used for short-range communication, will allow the app to control the robot’s movements, such as moving forward, backward, and turning. This exercise provides practical experience in both hardware integration and app development, focusing on creating a user-friendly interface for mobile devices to control robotics systems.

## Materials
1. A computer running Arduino IDE and Chrome Browser
2. A smartphone running an Android OS with the MIT AI2 Companion App
3. RedBoard
4. Ultrasonic sensor
5. Two motors
6. Motor driver
7. Battery pack
8. Additional wires
9. A cable / adapter for connecting the smartphone to RedBoard
10. An HC-05 Bluetooth UART Module
11. Velcro strips
12. Binder clip


## Assembly Methods
**Objective 1: Assemble and Test Your Robot**

  Begin by attaching the wheels to the motors used in Lab 6. Align the motor and wheel assembly with the chassis and ensure proper alignment to prevent malfunctions during movement. Secure the battery pack on the bottom of the robot using velcro, ensuring it doesn’t make contact with the floor when the binder clip is installed. Verify the robot’s functionality by testing basic movements (forward, backward, right, left) through serial communications using the Arduino IDE serial monitor.
  The schematic for assembling the motor circuit is provided in figure 1 below.

<div align= "center">
<img src= "https://github.com/user-attachments/assets/4b8a9e11-0ed9-4751-8eaf-1036c17608a1" alt "Schematic 1" width="400"/>
<br>
<figcaption style="font-size: 16px; text-align: center;"> Figure 1: Motor circuit schematic from Lab 6. Obtained from (https://learn.sparkfun.com/tutorials/sparkfun-inventors-kit-experiment-guide---
v40/circuit-5b-remote-controlled-robot
 </figcaption>
</div>

<br>

   Once assembled, the RedBoard circuit created using schematic 1 should resemble what is shown in Figure 2 below. The wheels were attached on the underside of the RedBoard with velcro once circuit assembly was complete.

<div align= "center">
<img src="https://github.com/user-attachments/assets/707ffc2e-4e82-4dd4-90eb-d30b9c725e5c"
alt "Motor Circuit" width="400"/>
<br>
<figcaption style="font-size: 16px; text-align: center;"> Figure 2: Constructed motor circuit from Schematic 1. </figcaption>
</div>
<br>

**Objective 2: Develop the App**

   First, create an account and log into MIT App Inventor 2. Start a new project, then in the Designer section, add a button to start serial communication, a label to show data from the Arduino, and buttons for moving the robot (forward, backward, right, left) with at least three speed options. Add the Serial and Clock components to handle communication and timing. 
   For our app, a check box was used to select the speed of the motor, and then buttons indicate direction.The designer section results should be comparable to what is shown in Figure 3 below.

<div align="center">
<img src="https://github.com/user-attachments/assets/996ddd1f-7188-43e0-a5ec-eee48d613165" alt="Designer App" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 3: Designer section in MIT App Inventor 2 after adding the necessary components to the app. </figcaption>
</div>   

<br/>
   In the Blocks section, set the button to connect to the RedBoard and use WriteSerial to send movement commands. Once the app is ready, build it and install the APK on an Android phone using the QR code. The following figures 4-9 show the blocks written to control our group's motor from the remote app.

<br/>

<div align="center">
<img src="https://github.com/user-attachments/assets/fdcc6cc5-0e11-4987-83e2-28e197230d77" alt="Blocks 1" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 4: MIT App Inventor 2 blocks for intializing app (1/6). </figcaption>
</div> 

<br/>

<div align="center">
<img src="https://github.com/user-attachments/assets/876094b5-a43f-4748-bba7-ac4ad30037e3)" alt="Blocks 2" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 5: MIT App Inventor 2 blocks for left turn function (2/6). </figcaption>
</div> 

<br/>

<div align="center">
<img src="https://github.com/user-attachments/assets/29c8a2f8-f3c1-4f45-a3df-a64cefd595a1" alt="Blocks 3" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 6: MIT App Inventor 2 blocks for right turn function (3/6). </figcaption>
</div> 

<br/>

<div align="center">
<img src="https://github.com/user-attachments/assets/2aade032-af0d-41e7-9a58-5da7a6481b71" alt="Blocks 4" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 7: MIT App Inventor 2 blocks for forwards motor function (4/6). </figcaption>
</div> 

<br/>
<div align="center">
<img src="https://github.com/user-attachments/assets/e8487562-2b17-47db-8f7d-47299a50cfe5" alt="Blocks 5" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 8: MIT App Inventor 2 blocks for backwards motor function (5/5). </figcaption>
</div> 

<br/>


**Objective 3: Wireless Remote**

  Wire the HC-05 Bluetooth UART module on the breadboard. Use pins 2 and 3 for the Rx and Tx connections, incorporating a voltage divider with resistors between 1kΩ and 2kΩ to manage the signal levels. This setup ensures that the Bluetooth module communicates effectively with the robot’s RedBoard. The circuit with the HC-05 module added should resemble what is shown in Figure 9 below.

 <div align="center">
  <img src="https://github.com/user-attachments/assets/f1274774-c9dd-420f-9a06-b8f088f63156" alt="Bluetooth Motor Circuit" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 9: Motor Circuit with HC-05 Bluetooth UART module addition. </figcaption>
</div>
<br>

Upload the appropriate Arduino sketch to the RedBoard, ensuring that it supports Bluetooth communication and commands from the mobile app. Include the necessary code lines for establishing Bluetooth communication, setting up serial connections, and interpreting data commands sent from the app (such as direction and speed). The blocks added to the code to allow bluetooth connection are shown in Figure 10-12.

 <div align="center">
  <img src="https://github.com/user-attachments/assets/f38f9655-7803-4f0a-9ae7-42975c43a762)" alt="Bluetooth Blocks 1" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 10: Blocks added in MIT App Inventor 2 to enable bluetooth compatibility (1/3) </figcaption>
</div>

<br/>

<div align="center">
  <img src="https://github.com/user-attachments/assets/8759198d-5a3b-49d6-8283-190b65ae5850" alt="Bluetooth Blocks 2" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 11: Blocks added in MIT App Inventor 2 to enable bluetooth compatibility (2/3). </figcaption>
</div>

<br/>
<div align="center">
  <img src="https://github.com/user-attachments/assets/78d968b8-aec6-4d36-9c4a-630442359062" alt="Bluetooth Blocks 3" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 12: Blocks added in MIT App Inventor 2 to enable bluetooth compatibility (3/3). </figcaption>
</div>

<br/>


<br>

## Test Equipment

1. Fluke 87 V DMM
2. Computer with Arduino IDE
3. Oscilloscope
   
   
## Test Procedures

**Part 1: Assemble and Test Your Robot**
   
   Upload the Blink program (File > Examples > Basics > Blink) to the Arduino and verify that the LED blinks. Adjust the delay in the program to decrease the blinking speed until the LED appears to remain constantly illuminated.

   The code used for this portion of the lab is provided below:

<br>
*Script: blink_arduino*
<br/>
// the setup function runs once when you press reset or power the board
<br>
void setup() {
<br>
  pinMode(LED_BUILTIN, OUTPUT);        // initialize digital pin LED_BUILTIN as an output.
  <br>
}
<br/>

// the loop function runs over and over again forever
<br>
void loop() {
<br>
  digitalWrite(LED_BUILTIN, HIGH);     // turn the LED on (HIGH is the voltage level) 
  <br>
  delay(10);                           // wait for a second
  <br>
  digitalWrite(LED_BUILTIN, LOW);      // turn the LED off by making the voltage LOW
  <br>
  delay(10);                           // wait for a second
  <br>
}
<br/>

**Part 2: Develop the App**

   Upload the Analog Read Serial program (Examples > Basics > AnalogReadSerial) to the Arduino and open the serial monitor (Tools > Serial Monitor), ensuring the baud rate is set to 9600 bps. Adjust the potentiometer and observe the serial output. Modify the code to control the LED’s blinking time based on the potentiometer’s input, demonstrating how analog inputs can be converted into digital signals.

   The code used for this section of the lab is provided below:
<br>
*Script: AnalogReadSerial_Arduino_BlinkControl*
<br/>
/*
  AnalogReadSerial with LED Blink Control
<br>
  Reads an analog input on pin A0, prints the result to the Serial Monitor,
  and uses the value to set the blinking time of the built-in LED.
<br>
  Connect:
  <br>
  - The center pin of a potentiometer to A0.
  - One outer pin to +5V.
  - The other outer pin to GND.
<br>
*/
<br/>

// Define the pin for the LED
<br>
const int ledPin = LED_BUILTIN;            // Built-in LED pin (usually pin 10)
<br/>

// the setup routine runs once when you press reset:
<br>
void setup() {
<br>
  // Initialize serial communication at 9600 bits per second:
  <br>
  Serial.begin(9600);
  <br>
  // Set the LED pin as an output
  <br>
  pinMode(ledPin, OUTPUT);
  <br>
}
<br/>

**Part 3: Wireless Remote**
   Run the same program from the previous section and observe how different lighting conditions affect the analog values. Implement an if-else statement to turn on the LED only when the brightness sensed by the photoresistor is low. Experiment with blocking the light source and analyze the circuit’s response time by observing whether the LED turns on and off immediately.
   Figure 11 below shows the testing technique used by our group for blocking the photoresistor to turn on the LED.
   
   <div align="center">
  <img src="" alt="Potentiometer testing" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 11: Testing the photoresistor controlled circuit. </figcaption>
</div>
<br>

   The code used for this portion of the lab is provided below:


## Test Results:

**Table 1: LED Blinking Delay**

|               | Delay Setting | Blinking? |
|---------------|---------------|-----------|
| Original      | 1000          | Yes       |
| -14           | 500           | Yes       |
| -12           | 200           | Yes       |
| -5            | 100           | Yes       |
| 0             | 50            | Yes       |
| 5             | 30            | Yes       |
| 12            | 15            | Yes       |
| 14            | 10            | No        |

## Discussion:
**Part 1: Assemble and Test Your Robot**
<br>

Disc Q: In Lab 6 we found out what was the minimum speed that will move the motors.
What is the minimum speed that will move the complete car?

<br>

**Part 2: Develop the App**
<br>



<br>

**Part 3: Photoresistor Controlled Circuit**
<br>



<br>



## Conclusion:
This lab provided hands-on experience in microcontroller programming, sensor integration, and PWM signal control. The experiments demonstrated key principles of digital and analog signals, persistence of vision, and sensor-based input processing. The use of an oscilloscope to visualize PWM waveforms further reinforced the understanding of duty cycles and their effect on perceived LED brightness. These findings are essential for applications in embedded systems, electronic circuits, and real-world automation technologies.
