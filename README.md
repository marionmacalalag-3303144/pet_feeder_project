# 🐾 Automated Pet Feeder System

## Overview

This project simulates and designs a low-cost, programmable automated pet feeder for use in animal shelters. The system is capable of dispensing food at scheduled times, monitoring consumption, and alerting staff if any issues arise (e.g., food not dispensed, pet not present, food not eaten).

The goal is to create a reliable, scalable solution using affordable components such as servo motors, load cells, and basic sensors, with logic that can be implemented on microcontrollers like Arduino or ESP32.

---

## Features

- ⏰ **Scheduled Feeding**: Dispenses food at configurable times (e.g., 8:00 AM and 6:00 PM).
- ⚙️ **Servo-Controlled Dispensing**: Uses a motor to dispense precise portions.
- ⚖️ **Weight Monitoring**: Load cell measures bowl weight before and after feeding.
- 🐕 **Pet Presence Detection**: Optional sensor to detect if the pet is nearby.
- 📊 **Consumption Tracking**: Monitors whether food has been eaten within a set time window.
- 🚨 **Alert System**: Sends notifications to staff if feeding fails or food is untouched.
- 💾 **Data Logging**: Stores feeding events, sensor readings, and alerts in a database or cloud service.
- 💡 **Status Indicators**: Visual feedback via LEDs (e.g., green for success, red for error).

---

## Hardware Requirements

| Component             | Description                          |
|----------------------|--------------------------------------|
| Microcontroller       | ESP32, Arduino Uno, or Raspberry Pi |
| Servo Motor           | SG90 or equivalent                   |
| Load Cell + HX711     | For bowl weight measurement          |
| Food Level Sensor     | IR or ultrasonic sensor              |
| Pet Presence Sensor   | PIR, RFID, or BLE beacon             |
| LED Indicator         | RGB LED or Neopixel strip            |
| Wi-Fi Module          | Built-in (ESP32) or external         |
| Power Supply          | 5V/12V adapter or battery pack       |

---

## Software Requirements

- Arduino IDE or PlatformIO (for microcontroller code)
- Python (for simulation or Raspberry Pi implementation)
- Firebase / Google Sheets API (for cloud logging)
- Twilio / SMTP (for alerts via SMS or email)

---

## Installation & Setup

1. **Hardware Assembly**
   - Connect servo motor to dispensing mechanism.
   - Mount load cell under feeding bowl.
   - Install sensors for food level and pet presence.
   - Connect components to microcontroller.

2. **Software Deployment**
   - Flash the microcontroller with the feeder logic.
   - Configure feeding times, portion sizes, and thresholds.
   - Set up cloud logging and alert services.

3. **Testing**
   - Calibrate load cell.
   - Simulate feeding cycles.
   - Verify alerts and data logging.

---

## Logic Flow Summary

```text
1. At scheduled time (e.g., 8AM or 6PM), check if feeding has occurred.
2. If not:
   - Rotate servo to dispense food.
   - Measure bowl weight before and after.
   - Verify food was dispensed successfully.
   - Check pet presence (optional).
   - Wait 10–45 minutes and monitor bowl weight.
   - If food was eaten, log success and show green light.
   - If not, trigger alert and show red light.
