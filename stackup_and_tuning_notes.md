# Stackup, Impedance, and Tuning Notes

## 50 Ohm Trace

The board uses a 3.0 mm top-layer RF trace over a continuous bottom-layer ground plane. For a typical 1.6 mm FR-4 board with Er around 4.2 and 1 oz copper, this is in the practical range for a 50 ohm microstrip.

For tighter impedance control, ask the fabricator for the actual dielectric height and Er, then re-calculate trace width in KiCad's PCB Calculator or a field solver.

## SMA Launch

The SMA launch uses a wide center pad with adjacent ground pads and via stitching near the connector. The short transition from the launch pad into the RF trace should be tuned against the exact edge-launch connector datasheet.

Keep solder mask pulled back from the launch copper if your SMA connector application note recommends it.

## L-Network

The starting matching network is:

- C1: 100 pF input DC block
- L1: 3.9 nH series inductor
- C2: 1.2 pF shunt capacitor to ground
- C3: 100 pF output DC block

These values are placeholders for a plausible 2.4 GHz amplifier input match. Replace them with values from the selected amplifier S-parameters and tune after assembly.

## VNA Tuning Flow

1. Calibrate at the SMA plane.
2. Measure the unpowered input match if the amplifier datasheet permits it, or bias the amplifier per datasheet for active S-parameter measurement.
3. If the S11 minimum is low-frequency shifted, reduce series inductance or shunt capacitance.
4. If the S11 minimum is high-frequency shifted, increase series inductance or shunt capacitance.
5. Confirm S11 below -15 dB across 2.4 GHz to 2.5 GHz.
6. Confirm S21 is flat enough for the system budget.

## DRC / Gerber

KiCad was not available in this runtime, so exported Gerbers are intentionally not included. Open `rf_2p4_front_end.kicad_pro` in KiCad, refill zones, run DRC, and export Gerbers/drill files from KiCad after selecting exact production footprints.

