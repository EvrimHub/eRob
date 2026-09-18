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
**Systems/reliability**

| ID   | Requirement                                                                          | Priority |
|------|----------------------------------------------------------------------------------------|----------|
| NR-01 | reflex layer works standalone without the Pi | Must |
| NR-02 | system runs untethered for a defined session length | Must |

**Electrical**

**Mechanical**

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
