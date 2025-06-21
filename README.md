# 🌱 Smart Watering Pot

The **Smart Watering Pot** is an automated plant watering system designed to monitor soil moisture and deliver the right amount of water to your plants—so they stay healthy even when you're away! This project integrates sensors, microcontrollers, and simple logic to take care of your greenery intelligently.

## 🎥 Demo

Check out the full video demonstration here:

[![Smart Watering Pot Demo](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://drive.google.com/file/d/1hz0x3sRglbCHoY4dQrAdUuLIgjunMBsg/view?usp=sharing)

*Note: Since the video is hosted on Google Drive, click the link above to view it.*

## 🌟 Features

* 🌡️ **Soil Moisture Monitoring** – Real-time data collection using a soil moisture sensor.
* 💧 **Automatic Watering** – Triggers watering when soil is too dry.
* 📦 **Compact & DIY Friendly** – Built with readily available components.
* 🔋 **Low Power Consumption** – Ideal for long-term unattended use.

## 🧰 Hardware Used

* Arduino (or compatible microcontroller)
* Soil Moisture Sensor
* Water Pump
* Relay Module
* Tubing
* 12V Power Supply (or battery)

## 💡 How It Works

1. The soil moisture sensor checks the moisture level.
2. If moisture drops below the threshold, the Arduino activates the pump via a relay.
3. Water is dispensed for a preset time, then automatically turned off.

## 🚀 Getting Started

1. **Clone this repo**:

   ```bash
   git clone https://github.com/your-username/smart-watering-pot.git
   cd smart-watering-pot
   ```
2. **Upload the code** to your Arduino using the Arduino IDE.
3. **Assemble the hardware** as per the included wiring diagram.
4. **Power it up**, and let your Smart Pot handle the watering!

## 📁 Project Structure

```
smart-watering-pot/
├── images/                # Circuit diagrams and build photos
├── SmartWatering.ino      # Arduino source code
├── README.md              # Project documentation
```

## 📸 Gallery

*(Optional: Add screenshots, wiring diagrams, or a gif here)*

## 🛠️ Future Improvements

* Add Wi-Fi monitoring (ESP8266/ESP32)
* Schedule-based watering
* Mobile notifications
