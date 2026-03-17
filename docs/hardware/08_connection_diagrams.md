# 8. Connection Diagrams

This chapter provides simplified public wiring references for common DUILIO F4 use cases.
The diagrams are intentionally simplified and must be adapted to the actual system.

## 8.1 Minimal bench setup

Use this setup for first power-up, USB communication, and initial diagnostics.
Do not connect motor power during the first validation step.

```
PC / USB Host
      |
      | USB data + logic power
      v
  DUILIO F4
```

## 8.2 PWM / DIR driver example

The following public reference image shows a typical DUILIO F4 connection to a PWM / DIR style motor driver.

![PWM DIR driver example](../images/schema_zs_x11.svg)

Practical rules:

- motor power remains external
- DUILIO F4 provides logic-level command signals only
- use a shared ground between board and driver
- ENABLE is recommended when the driver supports it

## 8.3 Dual-PWM / closed-loop example

The following public reference image shows a dual-PWM / servo-style example with external feedback devices.

![Dual PWM closed-loop example](../images/schema_servo_bts6970.svg)

Practical rules:

- validate voltage compatibility for every connected peripheral
- check current consumption of sensors and accessories against the board 5 V budget
- test closed-loop behavior without mechanical risk during the first setup

## 8.4 RC receiver setup

An RC receiver can be connected to the RC input group using the documented input pins and a valid shared reference.

```
RC Receiver
   |   PWM CH1..CH4 -------->  DUILIO F4 RC inputs
   |   +5 V ---------------->  RC / auxiliary 5 V if that power scenario is intended
   |   GND ----------------->  GND
```

WARNING: Do not treat every 5 V pin near the RC area as a generic unlimited supply rail.

## 8.5 Raspberry Pi integration

Raspberry Pi integration can use the documented host-side serial path and the optional 5 V relationship defined by the selected power configuration.

```
Single intended 5 V source
        |
        +----> Raspberry Pi 5 V
        |
        +----> DUILIO F4 5 V path (if intentionally configured)

Communication:
Raspberry Pi  <---- supported serial path or USB ---->  DUILIO F4
```

WARNING: Review power direction, jumper state, and back-powering risk before connecting USB to either device.

## 8.6 Common wiring mistakes

These mistakes are responsible for many integration failures:

```
1) Missing GND
DUILIO F4  ---- PWM/DIR ---->  Driver
           (no ground reference)

2) Motor power routed through DUILIO F4
Motor supply ---> DUILIO F4 ---> Motor/Driver

3) More than one active 5 V source
USB 5 V + external 5 V + Raspberry Pi 5 V

4) Accessory rail overloaded
Too many sensors / RC devices / host loads on the shared 5 V budget
```
