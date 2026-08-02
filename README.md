# four-DC(Servo-Ultrasoni)

## 🎥 Demo Video (Speeded-up \to parts)
https://github.com/user-attachments/assets/b821a43d-bf6f-4e13-9b0c-9085424df180


https://github.com/user-attachments/assets/3d133d95-a482-42a3-b76a-225ad3047916


## Project Overview
This project demonstrates how to control four DC motors using an Arduino Uno and two L293D motor driver ICs. The program performs a sequence of movements automatically without requiring any user input.

## Components
- Arduino Uno
- 2 × L293D Motor Driver IC
- 4 × DC Motors
- Breadboard
- Jumper Wires
- External Power Supply (if needed)

## Motor Pin Configuration

| Motor | L293D Driver | Pins |
|-------|--------------|------|
| Motor 1 | Driver 1 | IN1 (Pin 3), IN2 (Pin 2) |
| Motor 2 | Driver 1 | IN3 (Pin 5), IN4 (Pin 4) |
| Motor 3 | Driver 2 | IN5 (Pin 7), IN6 (Pin 6) |
| Motor 4 | Driver 2 | IN7 (Pin 9), IN8 (Pin 8) |

## Objective


The objective of this project is to control four DC motors and perform the following actions:

1. Move forward for 30 seconds.
2. Move backward for 60 seconds.
3. Turn right and left alternately for 60 seconds.
4. Stop all motors after completing the sequence.

## Program Logic
The Arduino program executes the following sequence:

1. Drive all four motors forward for 30 seconds.
2. Reverse all four motors for 60 seconds.
3. Rotate right and left alternately every 5 seconds for a total of 60 seconds.
4. Stop all motors.





## Part 2: Upgrade — Adding Ultrasonic Sensor + Servo Motor

### 🎥 Demo Video (After Upgrade)

https://github.com/user-attachments/assets/5c1e538a-fbed-4aba-8790-0687d88cbbc7






### What Was Added

- 1 × Ultrasonic Distance Sensor (3-pin type, single signal pin)
- 1 × Servo Motor

This upgrade turns the robot from a **fixed timed-motion demo** into an **autonomous obstacle-avoiding robot** that reacts to its environment in real time.

### Additional Pin Mapping

|Component              |Pin   |
|-----------------------|------|
|Servo (Signal)         |Pin 11|
|Ultrasonic Sensor (SIG)|Pin 10|

### Behavior Logic

1. The robot moves forward as long as no obstacle is detected
1. When an obstacle is detected, it stops immediately, reverses, then scans left and right with the servo-mounted sensor
1. It enters a waiting loop that keeps the motors fully stopped and continuously re-checks the distance — it will **not** move forward until the obstacle is confirmed gone
1. Once the obstacle is gone, the robot automatically resumes moving forward

> **Note on sensor logic:** This particular 3-pin sensor produces a **reversed reading** — the closer the object, the **larger** the number returned, unlike typical ultrasonic sensors. That’s why the code checks `distance >= 200` instead of a typical `distance <= 10` threshold.

-----

## Summary

|Stage |Behavior                                                       |
|------|---------------------------------------------------------------|
|Part 1|Timed motion demo (forward → backward → turns → stop)          |
|Part 2|Autonomous obstacle avoidance using ultrasonic + servo scanning|




