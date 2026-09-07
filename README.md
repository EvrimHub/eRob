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

| Layer            | Technology                                |
|-------------------|-------------------------------------------|
| Sensor node       | ESP32, FreeRTOS, PlatformIO, DHT22 sensor |
| Gateway OS        | Buildroot (optionally Yocto later)        |
| Communication     | MQTT (Mosquitto broker)                   |
| Data storage      | SQLite / InfluxDB                         |
| Visualization     | Grafana                                   |

## Project structure

```
bosporus/
├── README.md
├── docs/
│   ├── architecture.md      # Detailed system architecture
│   ├── requirements.md      # Functional & non-functional requirements
│   ├── project-plan.md      # Phases, milestones, timeline
│   ├── progress-log.md      # Dated build log with photos/screenshots
│   ├── risk-register.md     # Risks and mitigations
│   ├── glossary.md          # Abbreviations and terms used
│   └── images/              # Photos and screenshots from the build
├── sensor-node/              # Firmware for the ESP32 (to follow)
├── gateway/                   # Buildroot configuration, scripts (to follow)
└── dashboard/                 # Grafana configuration / web UI (to follow)
```

## Status

🔧 In progress – project for the targeted refresh of embedded knowledge as part of a
technical project leadership role in the embedded space.

## Motivation

As a technical project lead in the embedded space – including hands-on development
experience of my own, such as a C++ application on an embedded Linux board with an
AVR32 processor – it matters to me not just to coordinate technical work, but to
understand it from practical experience: cross-compiling, bootloader/kernel, toolchains,
component supply chains, testing strategies.

This project brings that understanding up to the current state of the art – from modern
build systems to today's development workflows – and serves as practical evidence of
this competence for a technical project leadership role in the embedded space.
