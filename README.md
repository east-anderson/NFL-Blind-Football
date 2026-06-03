# NFL Blind Flag Football

## Overview

NFL Blind Flag Football is an accessible smart football capstone project designed to help athletes with blindness or low vision locate, track, and interact with the ball during play.

The prototype is a rechargeable football with variable auditory and haptic feedback. It uses embedded electronics inside the ball to communicate the ball’s location and state through sound, vibration, motion sensing, Bluetooth-based proximity detection, and a paired mobile app.

This project was developed as part of a mission to make flag football more accessible and inclusive for athletes with varying levels of vision.

## Motivation

Football is one of the most popular sports in the United States, but accessibility in football remains an underexplored area. For athletes with blindness or low vision, tracking the ball visually can be difficult or impossible.

This project addresses that challenge by adding feedback systems directly into the football. The ball uses sound and vibration to help players understand where the ball is, whether it has been thrown, and when it is approaching important field elements such as an end zone or out-of-bounds boundary.

## Key Features

- Rechargeable smart football with embedded electronics
- Variable auditory feedback to signal the ball’s state
- Low-frequency drone when the ball is carried
- High-frequency pulse beeping when the ball is airborne
- IMU-based airborne detection using acceleration and angular velocity
- Haptic feedback for proximity-based field awareness
- Bluetooth RSSI-based distance sensing between the ball and field elements
- Haptic vibrations that begin within approximately 10 meters and increase with proximity
- Battery level monitoring using ADC measurements
- Paired accessible mobile app that displays the ball’s battery status
- Custom charging circuit with USB-C charging
- Accessible on/off switch
- Bluetooth pairing button
- LED battery indicator
- Design focus on accessibility, safety, durability, and feedback perceptibility

## System Architecture

The system is built around an internal microcontroller and custom PCB. The football integrates sensing, feedback, power, charging, and wireless communication into a compact internal system.

At a high level, the system includes:

- Raspberry Pi Pico 2W microcontroller
- Custom PCB
- 6-axis IMU / motion sensor
- Buzzer for auditory feedback
- Haptic motors for vibration feedback
- BLE communication for proximity sensing
- Rechargeable battery
- USB-C charging circuit
- Battery monitoring circuit
- LED indicator
- Mobile app interface
- External field element or beacon

```text
                  +-------------------------+
                  |   Accessible Mobile App |
                  |   Battery Status        |
                  +-----------^-------------+
                              |
                              | Battery Data
                              |
+----------------------------------------------------------+
|                      Smart Football                      |
|                                                          |
|  +----------------------------------------------------+  |
|  | Custom PCB                                         |  |
|  | - Rechargeable USB-C charging                      |  |
|  | - On/Off switch                                    |  |
|  +-------------------------+--------------------------+  |
|                            |                             |
|                            | Power                       |
|                            v                             |     
|                  +---------------------+                 |     +--------------------------+
|                  | Internal            |<----------------+---- | Field Element / Beacon   |
|                  | Microcontroller     |                 |     | End Zone, Boundary, etc. |
|                  +----------+----------+                 |     +--------------------------+
|                             |                            |
|          +------------------+------------------+         |
|          |                  |                  |         |
|          v                  v                  v         |
|  +---------------+  +---------------+  +---------------+ |
|  | IMU Motion    |  | Buzzers       |  | Haptic Motors | |
|  | Sensor        |  | Audio Feedback|  | Vibration     | |
|  +---------------+  +---------------+  +---------------+ |
|                                                          |
+----------------------------------------------------------+
