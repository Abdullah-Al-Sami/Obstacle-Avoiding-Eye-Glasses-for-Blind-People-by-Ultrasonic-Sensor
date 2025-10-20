# 🦯 Obstacle Avoiding Eye Glasses for Blind People

### **Project Type:** Embedded Systems & Assistive Technology  
### **Tools & Components:** Arduino Uno, Ultrasonic Sensor (HC-SR04), Buzzer, Jumper Wires  
### **Programming Language:** Arduino C/C++  
### **Domain:** Digital Logic Design & IoT Prototyping  

---

## 📘 Project Description

**Obstacle Avoiding Eye Glasses** is a smart wearable device designed to assist visually impaired individuals in detecting nearby obstacles.  
Using an **ultrasonic sensor** for distance measurement and a **buzzer** for sound feedback, the system alerts the user of obstacles within a defined range, helping ensure safer navigation.

**(≈350 characters)**  
A smart wearable device using Arduino and ultrasonic sensors to detect obstacles for visually impaired users. It measures distance and triggers buzzer alerts when objects are close, assisting in navigation and safety. Built using Arduino Uno, HC-SR04 sensor, and basic digital logic design.

---

## 🎯 Objectives

- Develop a low-cost **assistive navigation device** for the blind.  
- Utilize **ultrasonic sensing** for distance detection.  
- Provide **audio feedback** through buzzer alerts.  
- Implement basic **digital logic** and Arduino control.  
- Demonstrate real-world application of **sensor interfacing**.

---

## 🧰 Components & Tools

| Component | Function |
|------------|-----------|
| **Arduino Uno** | Main microcontroller board |
| **HC-SR04 Ultrasonic Sensor** | Detects obstacle distance |
| **Buzzer** | Provides audio alert |
| **Jumper Wires** | Circuit connections |
| **Breadboard** | Prototype wiring |
| **Arduino IDE** | Programming and uploading code |

---

## ⚙️ Working Principle

1. The **ultrasonic sensor** emits sound waves and measures the time taken for the echo to return.  
2. The **Arduino** calculates the distance using the speed of sound.  
3. If an object is detected within a **preset threshold distance**, the **buzzer** is activated.  
4. The buzzer’s sound frequency or pattern changes based on proximity — closer obstacles produce faster beeps.  

---

## 🧩 Circuit Connections

| Component | Arduino Pin |
|------------|--------------|
| VCC (Sensor) | 5V |
| GND (Sensor) | GND |
| TRIG | Digital Pin 9 |
| ECHO | Digital Pin 10 |
| Buzzer (+) | Digital Pin 8 |
| Buzzer (−) | GND |

---

## 💻 Arduino Code (Example)
```cpp
#define TRIG 9
#define ECHO 10
#define BUZZER 8

void setup() {
  pinMode(TRIG, OUTPUT);
  pinMode(ECHO, INPUT);
  pinMode(BUZZER, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  long duration, distance;
  digitalWrite(TRIG, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG, LOW);
  duration = pulseIn(ECHO, HIGH);
  distance = (duration * 0.034) / 2;

  if (distance < 30) { // obstacle closer than 30 cm
    digitalWrite(BUZZER, HIGH);
  } else {
    digitalWrite(BUZZER, LOW);
  }
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  delay(200);
}
