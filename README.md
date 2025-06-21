# 🌿 Smart Watering Pot (NodeMCU + Blynk)

This project is an **IoT-based Smart Irrigation System** built with a **NodeMCU (ESP8266)**, a **soil moisture sensor**, and the **Blynk IoT platform**. It automates watering your plants based on real-time soil moisture readings and allows manual control via a mobile app.

## 📽️ Video Demonstration

▶️ [**Watch the Smart Watering Pot in Action**](https://drive.google.com/file/d/1hz0x3sRglbCHoY4dQrAdUuLIgjunMBsg/view?usp=sharing)

---

## 🚀 Features

* 🌡️ **Soil Moisture Monitoring** – Real-time sensor readings sent to the Blynk app.
* 💧 **Automatic + Manual Watering** – Automated logic + app-based control via virtual button.
* 📱 **Blynk IoT Integration** – Control and monitor your plant from anywhere.
* ⚡ **Low Power Microcontroller** – Runs on NodeMCU (ESP8266).

---

## 🧰 Hardware Components

| Component                                           | Description                   |
| --------------------------------------------------- | ----------------------------- |
| NodeMCU (ESP8266)                                   | Wi-Fi-enabled microcontroller |
| Soil Moisture Sensor                                | Analog moisture detection     |
| Relay Module / Transistor + Motor                   | Controls water pump           |
| Mini Water Pump                                     | Delivers water to the plant   |
| Tubing, Pot, Jumper Wires, Breadboard, Power Supply | etc.                          |

---

## 📲 Blynk Setup

1. Install the **Blynk IoT app** (Android/iOS).

2. Create a new template with:

   * **Virtual Pin V6** → Moisture Level (Display)
   * **Virtual Pin V2** → Motor Control (Button)

3. Use the following credentials in the code:

   ```cpp
   #define BLYNK_TEMPLATE_ID "TMPL3VFIWAiSE"
   #define BLYNK_TEMPLATE_NAME "Irrigation"
   #define BLYNK_AUTH_TOKEN "LPez6z-1lm217wWOka9ZebAARlIG5Mdp"
   ```

---

## 💻 Code Overview

```cpp
const int moistureSensorPin = A0;
const int motorPin = 4; // D2 on NodeMCU

void loop() {
  int moistureValue = analogRead(moistureSensorPin);
  int moisturePercentage = map(moistureValue, wet, dry, 100, 0);
  Blynk.virtualWrite(V6, moisturePercentage);
  delay(1000);
}

BLYNK_WRITE(V2) {
  int pinValue = param.asInt();
  digitalWrite(motorPin, pinValue ? HIGH : LOW);
}
```

* **Moisture Level** is sent to virtual pin `V6`.
* **Motor Control** is toggled with a button on `V2`.

> Full source code available in [`SmartWatering.ino`](./SmartWatering.ino)

---

## 🔌 Circuit Diagram

*(Optional: Insert wiring diagram or image here if available. I can help you make one too.)*

Basic connections:

* Soil sensor → A0
* Pump → D2 via transistor/relay
* Power → USB / 5V

---

## 🌱 Calibration

Update these values based on your sensor's readings in dry/wet soil:

```cpp
const int dry = 1;
const int wet = 400;
```

---

## 🛠️ Future Enhancements

* 🌐 Push alerts for critical moisture levels
* 🕒 Scheduled watering using timers
* 🌡️ Integrate temperature and humidity sensors
