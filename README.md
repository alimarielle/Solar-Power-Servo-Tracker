# Solar Power & Servo Tracker

A micro:bit project that uses the Climate Action / Forward Education kit to monitor electrical power and automatically adjust a servo motor (likely for a solar panel) based on power output.

## 🚀 Overview

This code measures real-time current and voltage to calculate electrical power. It uses a "seek" behavior where a servo motor rotates to find the position that yields the highest power. If the power falls below a certain threshold, the servo continues to scan; once significant power is detected, it displays a bar graph of the output.

## 🛠 Features

* **Real-time Power Calculation:** Uses the formula `P = I * V` (Power = Current * Voltage).
* **Automated Scanning:** The servo rotates in 10-degree increments to find the best angle for energy collection.
* **Visual Feedback:** * Displays a **Small Diamond** while scanning.
  * Displays a **Bar Graph** when power exceeds 0.3W.
* **Manual Reset:** Button A allows for an immediate reset of the servo position and power variables.

## 🕹 Controls

| Input | Action |
| :--- | :--- |
| **Button A** | Resets servo angle to 0° and clears power variable. |
| **Automatic** | Servo scans from 0° to 180° until power > 0.3W is detected. |

## 📋 Hardware Requirements

* [micro:bit V2](https://microbit.org/)
* [Forward Education (fwd) Breakout Board](https://forwardedu.com/)
* 1x Position Servo (connected to `left_servo` port)
* 1x Voltage/Current Sensor (connected to `voltage1` and `current1` ports)

## ⚙️ Setup & Installation

1. Open [MakeCode for micro:bit](https://makecode.microbit.org/).
2. Click on **Extensions** and search for `fwd-edu` to add the Forward Education blocks.
3. Switch to the **Python** editor and paste the commented code provided.
4. Download the code to your micro:bit.
