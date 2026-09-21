# Requirements – eRob

## Functional requirements

| ID   | Requirement                                                                          | Priority |
|------|------------------------------------------------------------------------------------------|----------|
| R-01 | After powering on, eRob shall start moving through the flat | Must |
| R-02 | eRob shall detect an obstacle before collision, at a defined distance threshold | Must |
| R-03 | eRob shall change direction away from a detected obstacle | Must |
| R-04 | eRob shall detect an edge/drop-off and move back before falling | Must |
| R-05 | eRob shall support manual remote control (override/teleoperation) | Must |
| R-06 | Detected objects/obstacles shall be made accessible to the user | Should |
| R-07 | eRob shall distinguish between multiple detection classes (e.g. wall, shoe, pet) | Must |

## Non-functional requirements

**Systems reliability**

| ID    | Requirement                                                                          | Priority |
|-------|------------------------------------------------------------------------------------------|----------|
| NR-01 | eRob shall avoid obstacles regardless of whether any higher-level processing (e.g. object recognition, navigation) is available, running, or has completed | Must |
| NR-02 | eRob shall be able to operate purely on its own onboard batteries, with no cable to anything external, for at least a defined minimum duration | Must |

**Electrical**

| ID    | Requirement                                                                          | Priority |
|-------|------------------------------------------------------------------------------------------|----------|
| ER-01 | eRob shall remain operational, with no unintended resets or malfunction of the logic/compute subsystem, during motor-induced load transients (e.g. stall current spikes) | Must |
| ER-02 | eRob's exposed surfaces shall not exceed 40°C during normal operation | Should |
| ER-03 | eRob shall use battery types requiring no special hazardous-handling procedures | Must |
| ER-04 | eRob's WiFi radios shall not noticeably degrade other household devices' WiFi performance | Should |
| ER-05 | eRob shall indicate to the user when battery level is low | Should |

**Mechanical**

| ID   | Requirement                                                                              | Priority |
|------|------------------------------------------------------------------------------------------|----------|
| M-01 | eRob's mechanical assembly shall remain rigid under motor torque and normal operating vibration | Must |
| M-02 | eRob's wheels shall rotate freely with no rubbing or binding against the chassis         | Must |
| M-03 | eRob shall move reliably across typical indoor flooring (hardwood, carpet, tile)         | Must |

## Out of scope (deliberately excluded from this version)

- No physical cleaning mechanism in v1 (vacuum motor, brushes, dustbin) — detection-only scope
- No SLAM or full mapping/navigation in v1 — reactive obstacle avoidance only
- No production-grade security hardening (same rationale as Bosporus: focus is on learning core principles)
- No cloud connectivity — local network only
- No custom PCB/enclosure design in v1 — breadboard/chassis-kit build is sufficient

## Notes for Technical Specification

- R-05 (manual remote control): implemented via MQTT commands published to a topic the ESP32 subscribes to
- R-06 (detections accessible to user): dashboard vs. file vs. other output method is a design choice, not fixed by the requirement
- ER-01 (load transient immunity): achieved via physically separate battery supplies for motor and logic/compute subsystems, with a shared ground reference
