# eRob – Robot Vacuum Portfolio Project

An end-to-end project to refresh and demonstrate skills for a Technical Project Manager role in Robotics or a embedded developer role in Embedded Systems design preferably in combination with Machine Learning. 

## Project goal

Within this project a small ROS2-based mobile robot, a robot vacuum,  with onboard perception will be developed to detect objects and obstacle. The physical cleaning function is out-of-scope of this project. The focus is proving the sensing, control, and recognition architecture a real robot vacuum would need.

## Architecture overview

The architecture comprises two layers. The layer with ESP32, motors and distance sensors for fast collision avoidance. This layer is the reflex layer. The layer with camera, object recognition (Raspberry Pi, ROS2 + ML) for smart object detection which requires mote time for calculate. This layer is decision layer, which is accordingly slower. 

```
Ultrasonic sensor  --> ESP32 (reflex layer)  -->  MQTT  --> Raspberry Pi (cognition layer) -->  Dashboard
                        - motor control                      - ROS2 nodes                        (Flask)
                        - obstacle avoidance                 - camera + ML object recognition
                        - closed-loop PID                    - publishes detection
```

Details in [docs/architecture.md](docs/architecture.md).

## Technologies used

| Layer                        | Technology                                      |
|------------------------------|-------------------------------------------      |
| Reflex layer                 | ESP32, FreeRTOS, PlatformIO, DC motor driver    |
| Actuation                    | TB6612FNG dual motor driver, 2x DC gear motors  |
| Distance Measurement         | HC-SR04 ultrasonic sensor                       |        
| Power supply                 | battery pack + USB power bank for the Pi        |
| Object recognition layer     | Raspberry Pi and ROS2                           |
| Data Transfer / Exchange.    | MQTT (Mosqutto).                                |
|Visualization.                | Flask Dashboard.                                |

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
├── Reflex layer/              # Firmware for the ESP32 (to follow)
├── Object recognition layer/  # ROS2 packages, ML interference
└── dashboard/                 # Flask dashboard
```

## Motivation

Hands-on evidence of technical depth for a technical project leadership role in Robotics, Embedded Systems Design with Machine Learning application.  
