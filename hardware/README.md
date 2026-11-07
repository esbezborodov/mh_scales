# Hardware

## Block diagram

![Block diagram](images/block-diagram.svg)

The original drawing to GOST 2.701-2008 (sheet E1, in Russian) is in
[drawings/E1-block-diagram.pdf](drawings/E1-block-diagram.pdf).

## Functional blocks

Mass is measured by three blocks: the load cell, the ADC and the microcontroller. The
accelerometer, the microcontroller and the tilt indicator form the leveling function. The
display shows the result, and two buttons control the tare.

| Block          | Component                         | Function                                                                  |
|----------------|-----------------------------------|---------------------------------------------------------------------------|
| Load cell      | 01022-010K-C3, single-point, 20 kg | Converts the load into a millivolt bridge signal                         |
| ADC            | HX711                             | Amplifies the bridge signal (PGA ×128) and converts it at 24-bit resolution; powers the bridge |
| Accelerometer  | ADXL345                           | Measures the gravity vector on three axes to find the tilt of the scale   |
| Microcontroller| MegaHunt MH1706                   | Reads the sensors, filters the data, computes mass and tilt, drives the display and the indicator |
| Display        | LCD1602 with I2C adapter          | Shows the mass and the status of the scale                                |
| Tilt indicator | LED                               | Warns the operator that the scale is not level                            |
| Tare button    | Panel push button                 | Adds the current load to the tare                                         |
| Zero button    | Panel push button                 | Clears the tare and returns to the calibrated zero                        |
| UART header    | Pin header                        | Firmware upload through the bootloader, debug output                      |

## Interfaces

| Link                        | Interface                         |
|-----------------------------|-----------------------------------|
| Load cell → ADC             | Differential bridge signal, filtered by an RC network |
| ADC → MCU                   | Two-wire serial (DOUT, PD_SCK)    |
| Accelerometer ↔ MCU         | I2C, interrupt lines INT1 and INT2 |
| MCU ↔ display               | I2C, shared with the accelerometer |
| MCU → tilt indicator        | GPIO                              |
| Buttons → MCU               | GPIO with pull-up resistors       |
| UART header ↔ MCU           | UART (RX, TX)                     |

## Power

The board is powered with 5 V through the USB mini-B connector. The MH1706 has an on-chip
regulator that supplies the 3.3 V rail for the ADC and the load cell, the accelerometer, the
buttons, the indicator and the UART. The display runs from 5 V.
