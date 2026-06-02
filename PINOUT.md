# DataFlyer 2650 — Pinout reference (26-pin IDC → 50-pin IDC)

## Assumed convention

The 26-pin IDC to 50-pin cable was first mapped out by highpuff
for his replacement cable for his Phase5 Blizzard IV SCSI kit.

When this PCB was designed it was confirmed that it was the same
for the Expansion Systems DataFlyer 1200 SCSI+.

## Full mapping table

| Signal     | IDC26 pin | IDC50 pin | DB25 pin |
|------------|-----------|-----------|----------|
| -REQ       | 1         | 48        | 1        |
| GND        | 2         | GND net   | 14       |
| -MSG       | 3         | 42        | 2        |
| -C/D       | 4         | 46        | 15       |
| -I/O       | 5         | 50        | 3        |
| GND        | 6         | GND net   | 16       |
| -RST       | 7         | 40        | 4        |
| -ATN       | 8         | 32        | 17       |
| -ACK       | 9         | 38        | 5        |
| GND        | 10        | GND net   | 18       |
| -BSY       | 11        | 36        | 6        |
| -SEL       | 12        | 44        | 19       |
| GND        | 13        | GND net   | 7        |
| -DBP       | 14        | 18        | 20       |
| -DB0       | 15        | 2         | 8        |
| -DB1       | 16        | 4         | 21       |
| GND        | 17        | GND net   | 9        |
| -DB2       | 18        | 6         | 22       |
| -DB3       | 19        | 8         | 10       |
| -DB4       | 20        | 10        | 23       |
| -DB5       | 21        | 12        | 11       |
| GND        | 22        | GND net   | 24       |
| -DB6       | 23        | 14        | 12       |
| TERMPWR    | 24        | 26        | 25       |
| -DB7       | 25        | 16        | 13       |
| GND (opt.) | 26        | GND net   | —        |

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
- **50-pin SCSI-1 connector pinout** — cdmediaworld.com SCSI pinout
  reference, "50-Pin Connector Pinout" section:
  <https://www.cdmediaworld.com/hardware/scsi/pinout.htm#50-Pin%20Connector%20Pinout>
- **IDC26-to-IDC50 mapping** — highpuff's replacement cable for the
  Phase5 Blizzard IV SCSI kit: <https://ikod.se/scsi-cable>
- **DataFlyer SCSI+ Users Manual**, page 33 — confirms the DB25 column
  matches Expansion Systems' implementation
