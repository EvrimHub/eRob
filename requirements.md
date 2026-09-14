# Requirements – Synapse

## Functional requirements

| ID   | Requirement                                                                          | Priority |
|------|----------------------------------------------------------------------------------------|----------|
| F-01 | The reflex node (ESP32) drives two DC motors via the TB6612FNG driver                  | Must     |
| F-02 | The reflex node measures distance to obstacles using the HC-SR04 ultrasonic sensor     | Must     |
| F-03 | The reflex node can be manually driven (teleoperation) via MQTT commands               | Must     |
| F-04 | The reflex node autonomously stops/turns to avoid an obstacle within a threshold range | Must     |
| F-05 | The reflex layer functions standalone, with no dependency on the Pi being online       | Must     |
| F-06 | The cognition node (Pi) runs ROS2 and bridges to the ESP32 via MQTT                    | Must     |
| F-07 | The cognition node captures camera frames and runs on-device object recognition        | Must     |
| F-08 | Detected objects/obstacles are published as ROS2 topics                                | Should   |
| F-09 | A dashboard displays live camera feed, detected objects, and robot status              | Should   |
| F-10 | Multiple detection classes can be distinguished (e.g. wall, shoe, pet)                 | Could    |
| F-11 | A physical cleaning mechanism is added                                                 | Could (deferred) |

## Non-functional requirements

| ID    | Requirement                                                                            |
|-------|------------------------------------------------------------------------------------------|
| N-01  | Motor power and logic/compute power are electrically isolated (separate battery packs)   |
| N-02  | The reflex layer's control loop runs with low, predictable latency (no ML/network dependency in the avoidance path) |
| N-03  | The system runs untethered (no wired power) for at least one continuous test session     |
| N-04  | The architecture is documented clearly enough that a third person can follow the reflex/cognition split |
| N-05  | Configuration and code are version-controlled and reproducible                           |
| N-06  | The build reuses Bosporus's ESP32 and Raspberry Pi without compromising Bosporus's own documented, working state |

## Out of scope (deliberately excluded from this version)

- No physical cleaning mechanism in v1 (vacuum motor, brushes, dustbin) — detection-only scope
- No SLAM or full mapping/navigation in v1 — reactive obstacle avoidance only
- No production-grade security hardening (same rationale as Bosporus: focus is on learning core principles)
- No cloud connectivity — local network only
- No custom PCB/enclosure design in v1 — breadboard/chassis-kit build is sufficient
