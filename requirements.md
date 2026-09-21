# Requirements – Synapse

## Functional requirements

| ID   | Requirement                                                                          | Priority |
|------|----------------------------------------------------------------------------------------|----------|
| R-01 | After powering on, eRob starts moving through the flat | Must |
| R-02 | eRob detects an obstacle before collision, at a defined distance threshold| Must |
| R-03 | eRob changes direction away from a detected obstacle | Must |
| R-04 | eRob detects an edge/drop-off and moves back before falling | Must |
| R-05 | eRob supports manual remote control (override/teleoperation) — solution-agnostic version of the old "MQTT" bullet| Must |
| F-06 | Detected objects/obstacles are made accessible to the user — solution-agnostic version of the old "ROS2 topics / dashboard" bullets; how (dashboard vs. file vs. topic) is a design choice for the tech spec | Should |
| R-07 | Multiple detection classes can be distinguished (e.g. wall, shoe, pet) | Must |

## Non-functional requirements
**Systems reliability**

| ID   | Requirement                                                                          | Priority |
|------|----------------------------------------------------------------------------------------|----------|
| NR-01 | eRob avoids obstacles regardless of whether any higher-level processing (e.g. object recognition, navigation) is available, running, or has completed | Must |
| NR-02 | eRob must be able to operate purely on its own onboard batteries, with no cable to anything external, for at least some minimum duration. | Must |

**Electrical**

| ID   | Requirement                                                                          | Priority |
|------|----------------------------------------------------------------------------------------|----------|
| ER-01 | eRob shall remain operational, with no unintended resets or malfunction of the logic/compute subsystem, during motor-induced load transients (e.g. stall current spikes) | Shall |
| ER-02 | eRob's exposed surfaces shall not exceed 40°C during normal operation.| Shall |
| ER-03 | eRob shall use battery types requiring no special hazardous-handling procedures.| Shall |
| ER-04 | eRob's WiFi radios shall not noticeably degrade other household devices' WiFi performance.| Shall |
| ER-05 | eRob shall indicate to the user when battery level is low. | Shall |

**Mechanical**

| ID    | Requirement                                                                              | Priority |
|-------|------------------------------------------------------------------------------------------|----------|
| M-01  | Mechanical assembly must remain rigid under motor torque and normal operation vibration  | Shall    |
| M-02  | eRob's wheels must rotate freely with no rubbing or binding against the chassis          | Shall    |
| M-03  | eRob must move reliably across typical indoor flooring (hardwood, carpet, tile)          | Shall    |

## Out of scope (deliberately excluded from this version)

- No physical cleaning mechanism in v1 (vacuum motor, brushes, dustbin) — detection-only scope
- No SLAM or full mapping/navigation in v1 — reactive obstacle avoidance only
- No production-grade security hardening (same rationale as Bosporus: focus is on learning core principles)
- No cloud connectivity — local network only
- No custom PCB/enclosure design in v1 — breadboard/chassis-kit build is sufficient

Notes for Technical Specification

Load transient immunity (NFR-xx) is achieved via physically separate battery supplies for motor and logic/compute subsystems, with a shared ground reference. Spec for ER-01.



