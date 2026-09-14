# Project plan – eRob

## Phase overview

| Phase | Title                                | Content                                                                          | Milestone                                    | Status         | Start Date | Finish Date |
|-------|----------------------------------------|-------------------------------------------------------------------------------------|------------------------------------------------|----------------|------------|-------------|
| 0     | Preparation                            | Order chassis, motor driver, HC-SR04, resistor kit, motor battery pack, second deck plate + standoffs, power bank, multimeter | Hardware in hand                                | ✅ Done (all parts ordered/received) | WK 36 | WK 36|
| 1     | Chassis + motors, teleoperation        | Assemble chassis, wire motor driver to ESP32, minimal motor-control firmware, MQTT-driven teleoperation | Robot drives on manual command                  | 🔄 In progress — mechanical mounting complete (motors on acrylic clips with tape, wheels confirmed spinning freely under battery load), driver board soldered; still open: full ESP32↔driver↔battery wiring, test firmware, teleoperation | WK 37 | WK 38 |
| 2     | Reflex avoidance (ESP32 only)          | Add HC-SR04, implement immediate stop/turn avoidance logic, standalone from the Pi | Robot avoids obstacles with no Pi involved      | ⬜ Not started | WK 39 | WK 39 |
| 3     | ROS2 on the Pi                         | Set up ROS2, basic publish/subscribe nodes, bridge to ESP32 via MQTT               | Pi and ESP32 exchange messages over ROS2/MQTT   | ⬜ Not started | 27.09 | 28.09|
| 4     | Camera + object recognition            | Add camera module, run lightweight on-device ML model, publish detections          | Detected objects visible as ROS2 topic output   | ⬜ Not started | | |
| 5     | Dashboard                              | Reuse Flask pattern from Bosporus: live feed, detections, robot status             | Dashboard shows live robot state                | ⬜ Not started | | |
| 6     | Documentation & portfolio              | Finalize docs, clean up GitHub repo, write up architecture decisions               | Presentable project for job applications        | ⬜ Not started | | |
| 7     | (Deferred) Cleaning mechanism           | Add actual vacuuming hardware, if pursued                                          | Documented as future work                       | ⬜ Deferred    | | |

## Definition of done per phase

A phase counts as complete when:
1. the functionality demonstrably works (a short demo/photo/log),
2. the related configuration/code is version-controlled in the repo,
3. the documentation (README or the relevant docs/ file) has been updated.

## Notes

- Phases 1–2 are firmware-only and can be built and tested with the ESP32 powered over USB;
  the motor battery pack is only required once motors need to actually spin under their own power.
- Phase 6 mirrors Bosporus's own "Documentation & portfolio" phase — same discipline, dated log
  entries as the build happens rather than reconstructed afterward.
