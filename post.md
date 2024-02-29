# Lab 4: Exploring Sensor Integration

## Overview and Motivation
The purpose of this lab exercise is to explore the ways an Arduino and an embedded computer system can communicate and interact with the external environment. We introduced two sensors (devices which gather information from the external environment for the Arduino), and two actuators (a device through which the Arduino affects physical change in the external environment). We chose to design a Distance Detector as our project design. To design this project we had to build a handheld proximity detector that emits a sound whose pitch correlates with the distance to a nearby object.


## Materials

- PB-503 breadboard
- Wires
- Arduino kit
- Arduino controller with the USB adapter
- Computer for the Arduino IDE
- Buzzer
- Sensor

## Project Steps

We will split our project into two main sections. For each section, we will build the input and output and connect them together.

### 1. Building the input - Ultrasonic Sensor
- Plug the ultrasonic sensor to the auxiliary breadboard. It must go on the auxiliary board and not on the main breadboard because the proximity of other stuff on the breadboard will give us false echo readings.
- On one side of the sensor, on the pins, you will see names of what each pin represents.
- Connect the `+` pin (top pin) to +5V and the `-` pin (bottom pin) to GND on the Arduino.
- Connect the Trig pin to pin 13 on the Arduino. This will be the pin which turns on the sonar device (an output for your Arduino, an input for your sonar device).
- Connect the Echo pin to pin 2 on the Arduino. This will be the pin which reads the echo (input on Arduino, output on sonar device).

After following the steps above, you should be able to have something like this:

<img src="https://github.com/mlcourses/lab-4-blog-post-harisiqbal10/blob/main/assets/sensor.png" alt="alt text" width="400"/> 

### 2. Building the output - Buzzer
- Plug the buzzer onto the main breadboard so that the two pins span two distinct rows. Make sure the `+` pin is in the higher row (up) and the `-` pin is in the lower row (down).
- Use a wire to connect the `-` pin to GND. Make sure to also connect another wire from the GND on the breadboard to another GND on the Arduino. This is done to make sure that all of these connections have common ground.
- Plug the `+` end of the buzzer wire into Arduino pin 12.

After following the steps above, you should be able to have something like this:

<img src="https://github.com/mlcourses/lab-4-blog-post-harisiqbal10/blob/main/assets/buzzer.png" alt="alt text" width="400"/> 


## Testing

## Conclusion




