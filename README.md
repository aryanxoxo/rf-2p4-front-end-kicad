# 2.4 GHz RF Front-End KiCad Project

This is a real KiCad project scaffold for a compact 2.4 GHz RF front end, not a portfolio mockup.

## What Is Included

- `rf_2p4_front_end.kicad_pro`: KiCad project file with an RF netclass.
- `rf_2p4_front_end.kicad_pcb`: Two-layer PCB layout with board outline, edge-launch SMA pads, 50 ohm RF routes, 0402 matching parts, SOT-363 RF amplifier footprint, ground pours, and via stitching.
- `rf_2p4_front_end.kicad_sch`: Schematic intent sheet with the RF signal chain and starting component values.
- `stackup_and_tuning_notes.md`: Fabrication, impedance, and VNA tuning notes.

## Stackup Assumption

The PCB is set up for a common low-cost two-layer FR-4 stackup:

- Board thickness: 1.6 mm
- Copper: 1 oz outer
- Dielectric: FR-4, Er about 4.2
- Top RF trace width: 3.0 mm nominal for approximately 50 ohm microstrip over a solid bottom ground plane

If your board house uses a different stackup, update the RF track width before ordering.

## Important Fabrication Notes

Open the project in KiCad and run DRC before fabrication. KiCad is not installed in this Codex environment, so Gerbers were not exported or validated here.

Before ordering, replace the generic SMA edge-launch and SOT-363 amplifier footprints with the exact manufacturer land patterns for your selected connector and RF amplifier. The included geometry is suitable as an editable RF layout starting point.

## Suggested Bring-Up

1. Populate J1/J2, C1, L1, C2, C3, and U1.
2. Start with C1 = 100 pF, L1 = 3.9 nH, C2 = 1.2 pF, C3 = 100 pF.
3. Calibrate the VNA to the SMA reference plane.
4. Measure S11 and S21 from 2.3 GHz to 2.6 GHz.
5. Re-tune L1/C2 to center the match across 2.4 GHz to 2.5 GHz.

