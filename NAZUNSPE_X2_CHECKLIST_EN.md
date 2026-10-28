# Nazúŋspe-X2 – Commissioning Checklist

**Project:** Tenlog TL-D3 Pro Custom IDEX Rebuild  
**Goal:** A reliable Klipper-powered IDEX printer capable of printing with two different materials. Copy and Mirror modes come later.  
**Hardware:** BTT Manta M8P V2.0, TMC2240 drivers, two CAN toolheads, BERD-Air cooling.  
**Current setup:** Optical Z endstops and manual bed leveling; MicroProbe is not yet in use.

> **Status:** All checkboxes are intentionally unchecked. Mark a task with `- [x]` only after verifying it. Do not home Z while endstop detection is unreliable.

## 1. Klipper Base Configuration
- [x ] Verify all MCUs and CAN bus connections
- [x ] Check pin assignments and motor mapping
- [X ] Verify heaters, thermistors, and temperature limits
- [x ] Test fans, BERD-Air, and other outputs
- [x ] Test emergency shutdown and safety protections

## 2. Axes and Motion
- [x ] Test X0, X1, Y, and both Z motors individually
- [x ] Verify movement directions and `rotation_distance`
- [x ] Check microstepping, motor currents, and stepper drivers
- [x ] Determine mechanical travel limits
- [x ] Set conservative initial speeds and accelerations

## 3. Endstops and Homing
- [x ] Test every endstop using `QUERY_ENDSTOPS`
- [x ] **Verify reliable optical Z endstop detection**
- [x ] Test X0, X1, and Y homing individually
- [x ] Calibrate dual-Z homing and endstop phase after reliable detection is confirmed
- [x ] Check repeatability over multiple homing cycles

## 4. IDEX Base Configuration
- [ ] Verify `[dual_carriage]` and `safe_distance`
- [ ] Assign T0 and T1 correctly
- [ ] Define parking positions for both carriages
- [ ] Test T0/T1 tool changes without extrusion
- [ ] Verify collision-free motion sequences

## 5. Print Bed and Z Reference
- [ ] Heat the bed to operating temperature
- [ ] Level the bed mechanically
- [ ] Set the Z reference for T0
- [ ] Determine the T0/T1 nozzle height offset
- [ ] Verify the first layer independently for both toolheads

## 6. Extruders and Hotends
- [ ] Check extruder motors and feed directions
- [ ] Calibrate `rotation_distance` for both extruders
- [ ] PID-tune both hotends
- [ ] Verify filament feed and nozzle diameters
- [ ] Test extrusion and retraction behavior

## 7. Part Cooling
- [ ] Verify BERD-Air control and pump output
- [ ] Check airflow distribution around both nozzles
- [ ] Create PLA and PETG cooling profiles
- [ ] Monitor overcooling and warping
- [ ] Tune cooling for overhangs and bridges

## 8. Motion and Extrusion Calibration
- [ ] Check dimensional accuracy with calibration cubes
- [ ] Investigate vibrations and mechanical play
- [ ] Tune Input Shaper using measurements or test prints
- [ ] Calibrate Pressure Advance per extruder and material
- [ ] Gradually optimize speeds and accelerations

## 9. Slicer Setup
- [ ] Create an IDEX printer profile with two extruders
- [ ] Configure tool assignments and nozzle offsets
- [ ] Set start, end, and tool-change G-code
- [ ] Create material profiles for both extruders
- [ ] Configure purge lines, skirt, and prime tower if needed

## 10. Start, End, and Tool-Change Macros
- [ ] Configure `START_PRINT` for both extruders
- [ ] Test T0/T1 macros, including parking and activation
- [ ] Configure standby temperatures and retract/prime behavior
- [ ] Add purge lines for both tools
- [ ] Verify `END_PRINT`, carriage parking, and shutdown

## 11. Single-Material Test Prints
- [ ] Print a first-layer test using T0
- [ ] Print a first-layer test using T1
- [ ] Print calibration cubes separately with both extruders
- [ ] Check adhesion, warping, and surface quality
- [ ] Document working settings

## 12. Dual-Material IDEX Printing
- [ ] Prepare both materials
- [ ] Calibrate XY nozzle offsets with an alignment pattern
- [ ] Test repeated T0/T1 tool changes
- [ ] Minimize oozing and cross-contamination
- [ ] Complete a dual-material test print

## 13. Reliability and Error Handling
- [ ] Test pause and resume
- [ ] Verify filament changes and print cancellation
- [ ] Test idle timeout and stepper shutdown
- [ ] Check error handling and recovery where supported
- [ ] Run a longer print with multiple tool changes

## 14. Advanced IDEX Modes – Later
- [ ] Configure and test Copy mode
- [ ] Configure and test Mirror mode
- [ ] Verify safe distances and printable areas for each mode
- [ ] Create slicer profiles for both modes

## 15. Finalization and Documentation
- [ ] Back up the working configuration
- [ ] Verify GitHub backup and revision history
- [ ] Document macros and slicer profiles
- [ ] Record reference prints and calibration values
- [ ] Tag a stable configuration as a release

---

## Known Open Issues (2026-10-27)

- **Z endstop:** The sensor LED responded to interruption, but Klipper intermittently continued reporting `open`. Resolve signal detection before further Z homing.
- **First layer / PETG:** Check manual bed leveling and adhesion; a long printed part detached and warped.
- **IDEX macros:** Verify tool changes, end-of-print parking, and purge lines in an actual print sequence.
- **Priority:** Reliable normal dual-material printing before Copy/Mirror modes.

## Progress Log

| Date | Phase / Test | Result | Next Action |
|---|---|---|---|
| 2026-10-27 | Z endstop | Intermittently not detected by Klipper | Check signal path |
| 2026-10-27 | PETG test print | Adhesion and warping issues | Manually level the bed |
