# 🐾 Assignment 1 : Automated Pet Feeder System

## Overview

**Problem Statement** : A local animal shelter is currently facing challenges in ensuring timely and accurate feeding of their cats and dogs. Staff of the animal shelter are often preoccupied with other responsibilities which often lead to missed schedules for feeding. To improve overall efficiency and animal welfare there is a need to create a low cost programmable automated Pet Feeder System.

**Goal of the Automated Pet Feeder System** : Automate feeding of cats and dogs based on scheduled times and food consumption status, alerting staff to any food consumption issues or food dispensing issues. 

**Assumptions** : 
1. Feeding Schedule 
- Dogs and cats have the exact same feeding time which is pre assigned in the system
- Feeding occurs twice daily at fixed times : 8AM and 6:00PM
2. Food Consumption Monitoring 
- Weight Sensors are available to detect food consumption 
- Weight is logged from food dispensing time and 10 minutes after food dispensing.
- System can distinguish between consumed food vs spilled food 

3. Alert System 
- A red alert is triggered when one of the following happens : 
- No food is dispensed during a set time 
- Food is dispensed but pet did not eat 
- Pet is not present near the feeder

4. Feeder Types
- There are two types of feeders
- One for cats dispensing cat food
- One for dogs dispensing dog food.
- Each of the feeder follow the same decision logic and alters just a different type of food is dispensed 

5. Identification and registration 
- Only registered animals at the shelter are eligible for automatic food dispensing 
- There is a sensor in the feeder which indicates if a pet is currently present 


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

----


## Logic Flow Summary
---

## ⏰ 1. Read Current Time
- Retrieve the system’s current time using the real-time clock.

---

## 📅 2. Check Feeding Schedule
- If the time is **8:00 AM** or **6:00 PM**, proceed to dispense food.
- If not, keep the feeder inactive.

---

## 🍽️ 3. Dispense Food
- Activate the **servo motor** to dispense food into the bowl.
- Dispensed food type depends on feeder:
  - **Dog feeder** → Dispenses dog food
  - **Cat feeder** → Dispenses cat food

---

## 📦 4. Verify Dispense Success
- Check if the **food level in the container** is greater than 0%.
  - If **yes**:
    - Store the current food level and bowl weight in the database.
  - If **no**:
    - Trigger an **alert**.
    - Send an error message to staff indicating the dispense failed.

---

## 🐕 5. Check Pet Presence
- Detect whether the pet is currently present using motion or proximity sensors.
  - If **not present**:
    - Trigger an **alert** to staff indicating the pet is missing.
  - If **present**:
    - Proceed to monitor consumption.

---

## ⏳ 6. Monitor Consumption
- Wait **10 minutes** after dispensing.
- Retrieve the **starting bowl weight** from the database.
- Measure the **current bowl weight**.

---

## ⚖️ 7. Evaluate Consumption
- Calculate the difference between starting and current bowl weight.

### Logic:
- If **weight change = 0**:
  - Trigger an **alert**.
  - Send an error message to staff indicating the food was not eaten.
- If **weight change > 0**:
  - Display a **green light** on the feeder.
  - Send a success message confirming food was consumed.

---
