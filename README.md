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
