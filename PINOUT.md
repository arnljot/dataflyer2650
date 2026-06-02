# DataFlyer 2650 — Pinout reference (26-pin IDC → 50-pin IDC)

## Assumed convention

The 26-pin IDC to 50-pin cable was first mapped out by highpuff
for his replacement cable for his Phase5 Blizzard IV SCSI kit.

When this PCB was designed it was confirmed that it was the same
for the Expansion Systems DataFlyer 1200 SCSI+.

## Full mapping table

| IDC26 pin | DB25 pin | Signal     | IDC50 pin |
|-----------|----------|------------|-----------|
| 1         | 1        | -REQ       | 48        |
| 2         | 14       | GND        | GND net   |
| 3         | 2        | -MSG       | 42        |
| 4         | 15       | -C/D       | 46        |
| 5         | 3        | -I/O       | 50        |
| 6         | 16       | GND        | GND net   |
| 7         | 4        | -RST       | 40        |
| 8         | 17       | -ATN       | 32        |
| 9         | 5        | -ACK       | 38        |
| 10        | 18       | GND        | GND net   |
| 11        | 6        | -BSY       | 36        |
| 12        | 19       | -SEL       | 44        |
| 13        | 7        | GND        | GND net   |
| 14        | 20       | -DBP       | 18        |
| 15        | 8        | -DB0       | 2         |
| 16        | 21       | -DB1       | 4         |
| 17        | 9        | GND        | GND net   |
| 18        | 22       | -DB2       | 6         |
| 19        | 10       | -DB3       | 8         |
| 20        | 23       | -DB4       | 10        |
| 21        | 11       | -DB5       | 12        |
| 22        | 24       | GND        | GND net   |
| 23        | 12       | -DB6       | 14        |
| 24        | 25       | TERMPWR    | 26        |
| 25        | 13       | -DB7       | 16        |
| 26        | —        | GND (opt.) | GND net   |

## IDC50 ground net

Per the DataFlyer manual (page 33): **all odd pins except pin 25 are
connected to ground**. Additionally, the SCSI-1 reserved even pins
**20, 22, 24, 28, 30, 34** are also tied to GND on this board for
cleaner signaling and to match common SCSI-1 controller practice.

```
GND (odd, per DataFlyer manual):
     1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 27, 29, 31, 33, 35,
     37, 39, 41, 43, 45, 47, 49
GND (even, SCSI-1 reserved pins, tied for shielding):
     20, 22, 24, 28, 30, 34
NC:  25 (open per SCSI-1 spec)
TERMPWR: 26
```

## TERMPWR routing

- Routed from IDC26 pin 24 → IDC50 pin 26.
- Carries up to 1.5 A; the PCB routes this with 0.5 mm trace
  (other signals are 0.25 mm).

## References

- **DB25 SCSI pinout** — Amiga Hardware Reference Manual, section
  "External SCSI Disk DB25 Female (A3000 only)":
  <https://www.theflatnet.de/pub/cbm/amiga/AmigaDevDocs/hard_e.html#e-1-8>
  (theflatnet.de mirrors the old AmigaDevDocs)
- **IDC26-to-IDC50 mapping** — highpuff's replacement cable for the
  Phase5 Blizzard IV SCSI kit: <https://ikod.se/scsi-cable>
- **DataFlyer SCSI+ Users Manual**, page 33 — confirms the DB25 column
  matches Expansion Systems' implementation
