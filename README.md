# DataFlyer 2650 — 26-pin to 50-pin SCSI Adapter

A small PCB that plugs onto the 26-pin SCSI header of the Expansion Systems
DataFlyer 1200 SCSI+ controller card and exposes a standard 50-pin IDC SCSI
header on the opposite side, allowing connection to internal 50-pin SCSI
devices such as the BlueSCSI v2 Desktop.

If one uses a 90° angled female 26-pin IDC connector on the underside, it
can then be used with the Phase5 Blizzard IV SCSI kit instead.

## Initial work by highpuff @ ikod.se

This PCB was born from the need to have an BlueSCSI Desktop V2 mounted inside
an Amiga 1200 machine in a Checkmate 1500 plus cabinet with a DataFlyer 1200
SCSI+.

Googling for 26pin to 50pin solutions brought up the work by highpuff.
Go to his website [ikod.se/scsi-cable](https://ikod.se/scsi-cable) for the original cable.

From there the initial design was made one tuesday evening using KiCad and 
Freerouting.

## Physical design

- **J1 (26-pin IDC female, 2x13)**: mounted on the **bottom** side of the PCB,
  plugs directly down onto the SCSI controller card's 26-pin male header.
- **J2 (50-pin IDC male shrouded, 2x25)**: mounted on the **top** side of the PCB,
  accepts a standard 50-pin IDC ribbon cable to internal SCSI devices.
- **Silk screen**: the top 50-pin connector has a clear "PIN 1" arrow on the
  silk screen.

```
     ┌─────────────────────────────────┐
     │          ┌──────────────┐◄PIN 1 │
     │          │ J1: 26-pin   │       │  ← BOTTOM (B.Cu / B.SilkS)
     │          │ IDC female   │       │     plugs onto SCSI controller card
     │          │ (underside)  │       │
     │          └──────────────┘       │
     │                                 │
     │          ┌─────────────────┐    │  ← TOP (F.Cu / F.SilkS)
     │          │ J2: 50-pin IDC  │    │
     │          │  male shrouded  │    │
     │    PIN 1►└─────────────────┘    │
     └─────────────────────────────────┘
```

## Pinout source

The pinout mapping in this project is derived from:

1. The Apple/Amiga DB25 SCSI standard (also documented in the DataFlyer
   SCSI+ Users Manual, page 33)
2. The standard 50-pin SCSI-1 pinout
3. The IDC26-to-IDC50 mapping documented at iKod.se (originally for
   the Phase5 Blizzard IV SCSI kit, which uses the same convention)

See `PINOUT.md` for the full mapping table.

## Files

- `dataflyer-2650.kicad_pro` — KiCad 10 project file
- `dataflyer-2650.kicad_sch` — Schematic (rev 1.0, all 76 pins labeled)
- `dataflyer-2650.kicad_pcb` — PCB layout (rev 1.0, routed + GND zones)
- `PINOUT.md` — Pinout reference table
- `BOM.csv` — Bill of materials with Mouser part numbers
- `LICENSE.md` — Licensing notice (CERN-OHL-S-2.0)
- `CERN-OHL-S-2.0.txt` — Full text of the CERN-OHL-S-2.0 license

## Revision history

- **1.0** — Initial release.
- **1.1** — Bugfix: tie SCSI-1 reserved IDC50 pins (20, 22, 24, 28, 30, 34) to GND. PCB: J1 moved ~3.5 mm inboard for cleaner routing (does not affect mating with DataFlyer 1200 SCSI+ or Phase5 Blizzard IV SCSI kit).
- **1.1.1** — Patch (no GitHub release per the policy below). Front silkscreen overhaul: board name and revision now driven by `${BOARD_NAME}` / `${BOARD_REV}` project text variables, github URL added, attribution lines split for readability. J1 pin 1 marker added on bottom copper (B.Cu, mirrored, bold). No schematic or routing changes — electrically identical to 1.1.

## Release policy

Tagged GitHub releases are published only for **major** (`X.0`) and **minor**
(`X.Y`) versions. Patch versions (`X.Y.Z`) are committed to `main` only and aim
to remain production-ready — the Gerbers in the tree on any `main` commit
should be fabricable — but are not formally released.

## Bill of materials

See `BOM.csv`. Total cost per board ~$3-5 plus PCB fabrication.

## Termination

This adapter does NOT include termination resistors. The assumption is:

- The controller card itself terminates one end of the SCSI bus.
- The device at the far end of the 50-pin chain (e.g. BlueSCSI v2 Desktop)
  terminates the other end.


## Licensing

DataFlyer 2650 — 26-pin to 50-pin SCSI Adapter
Copyright (C) 2026 Arnljot Arntsen <arnljot_arntsen@hotmail.com>

Is licensed under CERN-OHL-S-2.0, see `LICENSE.md` for full details.
