# 🐾 Automated Pet Feeder System

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

```text
1. At scheduled time (e.g., 8AM or 6PM), check if feeding has occurred.
2. If not:
   - Rotate servo to dispense food.
   - Measure bowl weight before and after.
   - Verify food was dispensed successfully.
   - Check pet presence (optional).
   - Wait 10 minutes and monitor bowl weight.
   - If food was eaten, log success and show green light.
   - If not, trigger alert and show red light.
