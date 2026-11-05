# Requirements

Summary of the extended technical specification of the bachelor's thesis. The original
specification is in Russian; the values below are taken from it.

## Purpose

A packaging scale for check weighing, portioning of ingredients and packing of finished
products. The scale must stay accurate when it stands on an uneven surface, so it measures
its own tilt and helps the operator to level it.

## Functional requirements

| ID  | Requirement                                                                 |
|-----|-----------------------------------------------------------------------------|
| F1  | Measure the mass of an object and show it on the display in kilograms        |
| F2  | Read the load cell through an external ADC and filter the data digitally     |
| F3  | Tare: subtract the current load from the reading; each further press adds the current load to the stored tare |
| F4  | Zero: clear the stored tare and return to the calibrated zero               |
| F5  | Measure the tilt of the scale with an accelerometer                         |
| F6  | Warn the operator when the tilt exceeds the permissible angle               |
| F7  | Allow the scale to be leveled with adjustable feet                          |

## Metrological requirements

| Parameter               | Value                                        |
|-------------------------|----------------------------------------------|
| Minimum capacity        | 0.03 kg                                      |
| Maximum capacity        | 12 kg                                        |
| Maximum permissible error | ±2 g                                       |
| Accuracy class          | III per GOST R 53228-2008 (OIML R 76-1)      |

The load cell is rated for 20 kg. The maximum capacity is limited to 12 kg by the
stiffness of the 3D-printed plastic enclosure, even with the steel stiffening plate.

## Power

The scale is powered from the mains through an external 5 V adapter, so it can run
continuously without batteries. Power enters through a USB mini-B connector.

## Design constraints

| Parameter          | Value                         |
|--------------------|-------------------------------|
| Type               | Bench-top                     |
| Overall dimensions | within 300 × 300 × 200 mm     |
| Mass               | no more than 0.5 kg           |
| Unit cost          | no more than 3500 RUB         |

## Environmental requirements

| Condition              | Value                                           |
|------------------------|-------------------------------------------------|
| Climatic category      | UHL 4.1 per GOST 15150-69 (indoor use)          |
| Operating temperature  | +10…+25 °C                                      |
| Relative humidity      | up to 80 % at +25 °C                            |
| Transport vibration    | 1–80 Hz, 1 g                                    |
| Transport shock        | up to 15 g, pulse duration up to 6 ms           |

## Reliability and production

| Parameter                     | Value               |
|-------------------------------|---------------------|
| Mean time between failures    | at least 10 000 h   |
| Production volume             | 1500 units per year |
