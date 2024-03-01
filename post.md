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

### 3. Compiling and uploading the code

Type out and upload the following code to the Arduino and run it.

```c
#define BUZZER 12
#define TRIG 13
#define ECHO 2
void setup ()
{
  pinMode(BUZZER,OUTPUT);
  pinMode(TRIG,OUTPUT);
  pinMode(ECHO,INPUT);
  Serial.begin(9600);
  Serial.println("Start");
}
void loop () {
  Serial.println("Initiating Reading");
  digitalWrite(TRIG,HIGH);
  delay(10);
  digitalWrite(TRIG,LOW);
  int distance = pulseIn(ECHO,HIGH)/2;
  distance = distance / 29;  // tuning parameter
  Serial.print("Distance in cm is ");
  Serial.println(distance);
  if ((distance <= 100) and (distance >= 1)){
    tone(BUZZER,3000 - 25*distance)
  }
}
```
The above code:
- Defines pins for the buzzer and ultrasonic sensor (`TRIG` and `ECHO`).
- Initializes the buzzer as an output and the ultrasonic sensor pins appropriately.
- Begins serial communication to monitor distances measured by the sensor.
- Sends a pulse from the `TRIG` pin, waits for the echo on the `ECHO` pin, and calculates the distance based on the pulse duration.
- Converts the pulse duration to distance in centimeters, using a tuning parameter for accuracy.
- Prints the distance to the serial monitor.
- If an object is detected within 1 to 100 cm, activates the buzzer with a pitch inversely related to the distance (closer objects produce a higher pitch).

## Testing

After following the instructions described in the project steps (using the sensor as an input that connected to the arduino board, and the arduino output to the buzzer), we discovered that we got the desired results. We found out that the closer the object to the sensor, the higher the sound, and the further the object (the multimeter in this case) from the sensor, the lower the sound. That is exactly what we wanted and planned to see. Our code that combined both the code for the sound and the code for the distance, worked perfectly in designing the distance detector. The idea was to map between the distance and the sound in a way that if the distance away from the sensor is between 1 to 100 centimeters, we deduct from some reasonable decibels the distance times 25. The idea behind it was to ensure we have a good mapping that will lead to a situation where the closer the object to the sensor, the higher the sound and vice versa.

We were very happy to see that our combined code resulted in a great mapping that led to the desired outcome. It is important to mention that we could keep track of the distance both with the multimeter and also with the serial monitor in the arduino app on the computer. These tools were helpful for us to determine that our mapping was correct as we could see that the closer the distance of the multimeter to the sensor, the higher the sound from the buzzer, and the further the distance of the multimeter to the sensor, the lower the sound from the buzzer. 

Watch the videos below to observe how the Distance Detector's buzzer sound changes with proximity to objects, alongside an explanation of its configuration.

[Distance Detector Test](https://drive.google.com/file/d/1Ntirn4ES_KUPebDcAD13GqzaSIH69SPW/view?usp=sharing)
[Distance Detector Setup](https://drive.google.com/file/d/133IivIW7BGv7fh3NKNVhiUVJLwZuOFDW/view?usp=sharing)

## Conclusion

In this lab, we successfully merged the functionality of a buzzer with an ultrasonic sensor to create a dynamic Distance Detector. This integration not only demonstrated the Arduino's versatility in handling both input and output devices but also enhanced our understanding of interfacing with the physical world. By experimenting with sound frequencies in relation to object proximity, we have gained practical insights into sensor data manipulation and real-time feedback implementation. This lab has further solidified our foundation in embedded system applications, giving us the skills to build more complex and interactive projects in the future.



