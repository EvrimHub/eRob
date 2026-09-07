# eRob – Robot Vacuum Portfolio Project

An end-to-end project to refresh and demonstrate skills for a Technical Project Manager role in
Robotics or an embedded developer role in Embedded Systems design, preferably in combination with
Machine Learning.

## Project goal

Within this project, a small ROS2-based mobile robot — a robot vacuum — with onboard perception
will be developed to detect objects and obstacles. The physical cleaning function is out of scope
for this project. The focus is proving the sensing, control, and recognition architecture a real
robot vacuum would need.

## Architecture overview

The architecture comprises two layers. The **reflex layer** has the ESP32, motors, and distance
sensors for fast collision avoidance. The **cognition layer** has the camera and object
recognition (Raspberry Pi, ROS2 + ML) for smart object detection, which requires more time to
calculate and is accordingly slower.

```
Ultrasonic sensor  --> ESP32 (reflex layer)  -->  MQTT  --> Raspberry Pi (cognition layer) -->  Dashboard
                        - motor control                      - ROS2 nodes                        (Flask)
                        - obstacle avoidance                 - camera + ML object recognition
                        - closed-loop PID                    - publishes detections
```

Details in [docs/architecture.md](docs/architecture.md).

## Technologies used

| Layer             | Technology                                     |
|-------------------|-------------------------------------------------|
| Reflex layer      | ESP32, FreeRTOS, PlatformIO, DC motor driver    |
| Actuation         | TB6612FNG dual motor driver, 2x DC gear motors  |
| Distance measurement | HC-SR04 ultrasonic sensor                    |
| Power supply      | Battery pack + USB power bank for the Pi         |
| Cognition layer   | Raspberry Pi and ROS2                            |
| Data transfer / exchange | MQTT (Mosquitto)                          |
| Visualization     | Flask dashboard                                  |

## Project structure

```
eRob/
├── README.md
├── docs/
│   ├── architecture.md      # Detailed system architecture
│   ├── requirements.md      # Functional & non-functional requirements
│   ├── project-plan.md      # Phases, milestones, timeline
│   ├── progress-log.md      # Dated build log with photos/screenshots
│   ├── risk-register.md     # Risks and mitigations
│   ├── glossary.md          # Abbreviations and terms used
│   └── images/              # Photos and screenshots from the build
├── reflex-layer/             # Firmware for the ESP32 (to follow)
├── cognition-layer/          # ROS2 packages, ML inference (to follow)
└── dashboard/                 # Flask dashboard
```

## Motivation

Hands-on evidence of technical depth for a technical project leadership role in Robotics, or an
embedded systems design role in combination with Machine Learning.
