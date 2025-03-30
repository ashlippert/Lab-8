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
<img src="" alt "Schematic 1" width="400"/>
<br>
<figcaption style="font-size: 16px; text-align: center;"> Figure 1: Motor circuit schematic from Lab 6. Obtained from https://learn.sparkfun.com/tutorial/sparkfun-inventors-kit-experiment-guide---v40/circuit-3b-
distance-sensor
 </figcaption>
</div>

<br>

   Once assembled, the RedBoard circuit created using schematic 1 should resemble what is shown in Figure 2 below.

<div align= "center">
<img src="https://github.com/user-attachments/assets/d035d937-2607-494d-9e97-8ce2f591d9b5" alt "Schematic 1" width="400"/>
<br>
<figcaption style="font-size: 16px; text-align: center;"> Figure 2: Constructed LED circuit from Schematic 1. </figcaption>
</div>
<br>

**Objective 2: Develop the App**

**Potentiometer Controlled Circuit Assembly**

   Connect the potentiometer to 5V and Ground, with the variable resistance pin connected to A0. Keep the previous circuit intact while integrating the potentiometer into the setup. The schematic for this setup is given in Figure 3 and 4 below.


<div align="center">
<img src="https://github.com/user-attachments/assets/4cec5b73-a503-4f8a-9187-81eadedb0bf6" alt="Schematic 2" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 3: Potentiometer controlled LED circuit schematic. </figcaption>
</div>   

<br/>

<div align="center">
<img src="https://github.com/user-attachments/assets/f5ad3cd8-12cb-47c6-9d8f-ee0798607954" alt="Layout 2" width="400">
<br/>
<figcaption style="font-size: 16px; text-align: center;"> Figure 4: Potentiometer controlled LED circuit layout. </figcaption>
</div>   

<br/>

  Once assembled, the circuit should look resemble Figure 5 below.

   <div align="center">
  <img src="https://github.com/user-attachments/assets/23505952-297d-40d4-9144-ae91f7526852" alt="Assembled potentiometer controlled LED circuit" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 5: Constructed potentiometer controlled LED circuit from Figure 3. </figcaption>
</div>
<br>

**Objective 3: Wireless Remote**

**Photoresistor Controlled Circuit Assembly**

  Replace the potentiometer in the previous circuit with a series circuit consisting of a photoresistor and a 10 kΩ resistor. Connect 5V to the photoresistor, Ground to the resistor, and A0 to the node between them. The schematic and layout for this circuit is provided in Figure 6 and 7 below.

 <div align="center">
  <img src="https://github.com/user-attachments/assets/2d1a3739-0cca-4c5f-8fb9-16fd0eecc990" alt="Schematic 3" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 6: Photoresistor controlled LED circuit schematic. </figcaption>
</div>
<br>

 <div align="center">
  <img src="https://github.com/user-attachments/assets/e0e26917-4999-4354-8292-89b97e9d5812" alt="Layout 3" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 7: Photoresistor controlled LED circuit layout. </figcaption>
</div>
<br>

   Once assembled, the RedBoard circuit should resemble what is shown in Figure 8 below.
   
<div align="center">
  <img src="https://github.com/user-attachments/assets/bdb131cb-9715-411e-a1f5-6af3f370975d" alt="Assembled photoresistor controlled LED circuit" width="400">
      <br/>
  <figcaption style="font-size: 16px; text-align: center;"> Figure 8: Constructed photoresistor controlled LED circuit. </figcaption>
</div>
<br>


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
