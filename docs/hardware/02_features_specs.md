# 2. Features & Specifications

This chapter summarizes the public technical characteristics of DUILIO F4 from the point of view of installation, integration, and expected use.
It is not intended to expose the full private design package or detailed component-level design data.

## 2.1 Platform overview

Table 2-1 - Platform overview

| Parameter | Value | Notes |
| --- | --- | --- |
| Control core | STM32F411 | Board-level real-time control MCU |
| Product role | Motion control and I/O interface board | Intended to command external drivers, not to replace them |
| Motor axes | 2 | Two control channels per board |
| Primary control modes | RC, host-assisted, distributed node use | Final behavior depends on firmware profile and system integration |
| Main field interfaces | USB, UART, RS485, I2C, RC I/O | Public hardware-facing interfaces only |

## 2.2 Electrical specifications

Table 2-2 - Electrical specifications

| Parameter | Value | Notes |
| --- | --- | --- |
| Main supply input | 7-43 V DC | Intended VIN operating range |
| Absolute maximum input voltage | 51 V | Absolute maximum rating, not a normal operating target |
| Logic domains | 5 V and 3.3 V | Use peripherals compatible with the respective interface level |
| Main architecture | External motor power, onboard logic control | Motor power does not pass through DUILIO F4 |
| Auxiliary 5 V distribution | Available on dedicated connectors | Subject to total current budget and active power scenario |
| Analog inputs | 2 | Public user-facing analog inputs |
| RC inputs | 4 | RC-style PWM input channels |
| RC outputs | 4 | RC-style PWM output channels |

## 2.3 Motion and I/O capabilities

Table 2-3 - Motion and I/O capabilities

| Feature | Public description | Notes |
| --- | --- | --- |
| Motor driver control | PWM, DIR, ENABLE, BRAKE style interfaces | Depends on selected driver topology |
| Feedback inputs | RPM and sensor inputs available | Final use depends on firmware configuration |
| Digital outputs | Multiple low-side digital outputs | Intended for machine-level auxiliary functions |
| Sensor connectors | Dedicated sensor-style headers | Suitable for supported low-power peripherals |
| Host integration | Raspberry Pi and PC integration supported | Use public wiring rules and one intended power path |

## 2.4 Power and protection summary

Table 2-4 - Power and protection summary

| Parameter | Value | Notes |
| --- | --- | --- |
| VIN protection concept | TVS plus external fuse required | External fuse is part of the intended protection strategy |
| Input filtering and protection | Present on power and exposed interfaces | Intended to improve robustness against noise, wiring mistakes, and transients |
| 5 V rail protection | Resettable PTC protection | Limits overload current, does not replace correct sizing |
| Shared 5 V budget from VIN | Approx. 3 A continuous, 5 A peak | Shared across board auxiliary loads |
| Shared 5 V budget from USB or Raspberry Pi only | Typically less than 0.8 A | Depends on the actual source capability |
| Servo / auxiliary 5 V rail | Available on dedicated output group | Respect current limits and wiring recommendations |
| Raspberry Pi supply path | Less than 2 A continuous, 5 A peak | Applies only when the Raspberry Pi power path is intentionally enabled and the upstream source is adequate |

## 2.5 Environmental specifications

Table 2-5 - Environmental specifications

| Parameter | Value | Notes |
| --- | --- | --- |
| Operating environment | Technical indoor / sheltered use | Avoid uncontrolled outdoor exposure without enclosure |
| Humidity | Non-condensing | Avoid condensation and conductive contamination |
| Intended installation | Integrated into a larger system | Use standoffs, enclosure, and strain relief where appropriate |

## 2.6 Mechanical specifications

Table 2-6 - Mechanical specifications

| Parameter | Value | Notes |
| --- | --- | --- |
| PCB type | Rigid PCB | Intended for fixed mounting |
| Connector access | Edge-accessible | Keep cable routing compatible with the connector layout |
| Mounting concept | Mechanical fixing through dedicated holes | Use suitable spacers and insulation where required |
| Mechanical reference | See board drawing | Refer to Chapter 5 for the public dimension drawing |

## 2.7 Public status note

The current public documentation reflects the latest validated user-facing connector map, power architecture, and simplified integration guidance.
Photos and rendered views may be updated independently of the electrical documentation as the product presentation evolves.
