# NAZÚŊSPE X2 🪓

**Tenlog TL-D3 Pro Klipper Conversion by sun Dancer | Custom IDEX Rebuild | BTT Manta M8P V2.0 | Dual CAN Bus Toolheads**

### Two heads. One machine. A whole lot of stubbornness.

**NAZÚŊSPE X2** is a heavily modified, independently driven dual-extruder (IDEX) 3D printer built on the mechanical foundation of a **Tenlog TL-D3 Pro**.

*Forged from Tenlog. Rebuilt from scratch.*

> **Project status: Work in Progress (2026)**  
> The machine is being commissioned and calibrated. This repository is a record of an individual build, **not** a verified drop-in configuration for another printer.

## Tenlog TL-D3 Pro to Klipper: the rebuild

This GitHub repository documents a **Tenlog TL-D3 Pro Klipper upgrade and IDEX conversion**, including the BIGTREETECH Manta M8P V2.0 controller, TMC2240 stepper drivers, dual EBB42 CAN bus toolhead boards and custom toolheads. It is a personal engineering log, **not** an official Tenlog firmware release or ready-to-install upgrade kit.

## The story

This machine began life as a Tenlog TL-D3 Pro. Its original mechanical platform remains the starting point, but its control electronics, firmware and toolheads have been replaced or extensively reworked.

Both independent X carriages now carry custom-built toolheads. Their nozzle positions are not assumed to match the original Tenlog toolheads. Accordingly, the X-axis reference positions, travel limits and tool offsets are being measured and calibrated on the actual machine rather than copied from another build.

The name **Nazúŋspe** is a Lakota word for *axe* — a fitting name for a printer rebuilt into a distinctive working tool.

## Hardware

| Component | Configuration |
| --- | --- |
| Mechanical platform | Tenlog TL-D3 Pro (retained and modified) |
| Printer architecture | IDEX — independent dual X carriages |
| Mainboard | BIGTREETECH Manta M8P V2.0 |
| Host | Raspberry Pi CM4 |
| Stepper drivers | TMC2240 |
| Toolhead electronics | 2 × BIGTREETECH EBB42 Gen2, CAN bus |
| Toolheads | 2 × custom-modified assemblies |
| Firmware | Klipper |
| Web interface | Mainsail / Moonraker |
| Physical bed dimensions | 310 × 310 mm |
| Original advertised build volume | 300 × 300 × 350 mm |
| Configuration backup | Klipper-Backup → GitHub |

## Current progress

- [x] Replace the original controller with the Manta M8P V2.0
- [x] Set up Klipper, Moonraker and Mainsail
- [x] Integrate the independent X carriages and CAN toolhead electronics
- [x] Resolve motor wiring/pinout differences and verify axis motion
- [x] Establish initial physical X-bed-edge reference measurements
- [x ] Finalize X homing positions and travel limits for both carriages
- [x ] Calibrate toolhead offsets using the actual nozzle positions
- [ ] Complete remaining motion, bed and extrusion calibration
- [ ] Validate printing and IDEX operation

The checklist is a progress snapshot, not a guarantee that completed subsystems are ready for unattended printing.

## Configuration notes

The files in this repository are **specific to this machine**. They may contain pin assignments, motor directions, endstop polarity, CAN configuration, movement limits and heater settings that are unsafe or incorrect for other hardware.

**Do not flash or copy these settings to another printer without independently verifying the wiring, motion system and thermal protections.**

The original Tenlog TL-D3 Pro is commonly described as having a **300 × 300 × 350 mm build volume**. The physical bed on this machine measures **310 × 310 mm**. These dimensions are deliberately distinguished; the usable print area will be defined through calibration.

## Search terms and related hardware

Tenlog TL-D3 Pro, Tenlog TL-D3, Tenlog IDEX, Tenlog Klipper, Tenlog firmware conversion, Tenlog Manta M8P, dual carriage Klipper, EBB42 CAN bus, TMC2240, custom dual extruder 3D printer.

## Repository and backups

This repository is used to track and back up the Klipper configuration through **Klipper-Backup**. Configuration history reflects ongoing development and may include experiments or intermediate values.

## Rights and reuse

**© 2026 — NAZÚŊSPE X2 project. All rights reserved for original project materials unless expressly licensed otherwise.**

No permission is granted here for commercial reuse, redistribution or sale of original project materials without prior written authorization.

This notice applies only to material for which the project author holds the relevant rights. Klipper, other third-party software, contributed configuration fragments, hardware designs and the original Tenlog platform remain subject to their respective licenses and rights. Publishing this repository does not create exclusive rights over the general idea of rebuilding a 3D printer or over third-party designs.

If you plan to reuse any part of this repository, check the applicable file-level and upstream licenses first.

---

**NAZÚŊSPE X2 — Not just rebuilt. Reimagined.**
