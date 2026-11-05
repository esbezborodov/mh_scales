# mh_scales

Bench-top load cell scale with tilt calibration, built around the MegaHunt MH1706
microcontroller.

An HX711 24-bit ADC reads a single-point load cell, and an ADXL345 accelerometer checks
that the scale stands level. When the tilt is large enough to affect the reading, the scale
warns the operator, who levels it with the adjustable feet.

## Features

- Weighing range 0.03–12 kg with 1 g display resolution
- Cumulative tare: each press of Tare adds the current load to the tare, Zero clears it
- Tilt detection with a 3-axis accelerometer and a warning indicator
- 16×2 character LCD on the I2C bus
- Custom two-layer PCB, mostly surface-mount
- 3D-printed ABS enclosure with adjustable feet and a steel stiffening plate
- 5 V power over a USB mini-B connector

## Specifications

| Parameter            | Value                                   |
|----------------------|-----------------------------------------|
| Weighing range       | 0.03–12 kg                              |
| Maximum error        | ±2 g                                    |
| Display resolution   | 1 g                                     |
| Accuracy class       | III (GOST R 53228-2008, OIML R 76-1)    |
| Power supply         | 5 V DC, USB mini-B                      |
| Operating conditions | +10…+25 °C, up to 80 % RH               |
| Overall dimensions   | within 300 × 300 × 200 mm               |

The full list of requirements is in [docs/requirements.md](docs/requirements.md).

## Hardware

| Block         | Component                                              |
|---------------|--------------------------------------------------------|
| MCU           | MegaHunt MH1706, 32-bit RISC core, up to 80 MHz         |
| ADC           | Avia Semiconductor HX711, 24-bit sigma-delta, PGA ×128  |
| Load cell     | 01022-010K-C3, single-point, rated for 20 kg            |
| Accelerometer | Analog Devices ADXL345, 3-axis, I2C                     |
| Display       | LCD1602 with I2C interface                              |
| Indication    | Tilt warning LED                                        |
| Controls      | Tare and Zero buttons, reset button                     |
| Programming   | UART bootloader (boot jumper), SWD header               |

## Project history

The scale was my bachelor's thesis at Bauman Moscow State Technical University
(Department of Design and Production Technology of Electronic Equipment, IU4), completed
in spring 2026. Within the thesis I designed the electronics and the PCB in Altium
Designer and the enclosure in KOMPAS-3D, prepared the design documentation to GOST
standards, assembled a prototype and tested it with reference weights. The original
firmware was written in C for Keil MDK.

This repository publishes the design and continues the work on it:

- design documentation: block diagram, schematic, bill of materials, PCB and enclosure;
- firmware ported from Keil to the GNU Arm toolchain, refactored and built in CI;
- better signal processing: filtering, calibration and tilt compensation;
- the prototype re-tested over the full weighing range.

## Repository layout

```
mh_scales/
├── docs/          requirements, photos, test results
├── hardware/      block diagram, schematic, BOM, PCB, GOST drawings (PDF)
├── enclosure/     STEP and STL models, assembly drawing
├── firmware/      MH1706 firmware (C, GCC, CMake)
└── tools/         UART flashing utility
```

Folders are added as the corresponding part of the project is published.

## Status

- [x] Requirements
- [ ] Block diagram
- [ ] Schematic and bill of materials
- [ ] PCB
- [ ] Enclosure
- [ ] Firmware: GCC build and flashing tool
- [ ] Firmware: drivers and application
- [ ] Signal processing, calibration and tilt compensation
- [ ] Test results, v1.0

## License

Released under the MIT License, see [LICENSE](LICENSE).
