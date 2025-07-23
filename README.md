# Overview
An Arduino-based assistive device that helps visually impaired individuals detect obstacles using ultrasonic sensors. The device provides real-time haptic feedback through a buzzer or vibration motor when an object is detected within a specified range.

# Features

- Obstacle detection using ultrasonic sensors
- Buzzer alert for proximity warnings
- Easy to build and deploy
- Low-cost and effective

---

# Technologies & Skills Used

- **Arduino Programming**
- **Embedded Systems**
- **Sensor Integration**
- **Ultrasonic Sensing (HC-SR04)**
- **Prototyping and Testing**

---

# Hardware Components

| Component           | Quantity |
|---------------------|----------|
| Arduino UNO         | 1        |
| HC-SR04 Ultrasonic Sensor | 1  |
| Buzzer or Vibration Motor | 1 |
| 9V Battery + Clip   | 1        |
| Connecting Wires    | As needed |
| Breadboard          | 1        |
| Stick/Frame         | 1        |

---

# Circuit Diagram

![Smart Blind Stick Circuit Diagram](![alt text](<Arduino Circuit Diagram.png>)

---
## 💻 Arduino Code
#define trigPin 9
#define echoPin 10
#define buzzer 8

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzer, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  long duration, distance;

  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if (distance < 50) {
    digitalWrite(buzzer, HIGH);
  } else {
    digitalWrite(buzzer, LOW);
  }

  delay(500);
}

# Logic Summary

- Measure distance using ultrasonic sensor
- If distance is less than threshold (e.g., 50 cm), activate buzzer
- Else, buzzer remains off

---

# How to Run

1. Install [Arduino IDE](https://www.arduino.cc/en/software)
2. Open `smart_blind_stick.ino` in Arduino IDE
3. Select the correct board and port
4. Upload the sketch to your Arduino board
5. Connect your components as per the circuit diagram

---

# Output

Distance: 47 cm → Buzzer ON
Distance: 122 cm → Buzzer OFF
Distance: 18 cm → Buzzer ON

> 🔉 A buzzing sound/vibration occurs when obstacle is close

---

# Author
**Vidhi Mistry**  
vidhimistry@example.com  
