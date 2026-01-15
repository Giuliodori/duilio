# 8. Connection Diagrams
This chapter shows simplified, example-level wiring diagrams to illustrate safe integration. All diagrams are example only.

## 8.1 Minimal bench setup
Figure 8-1 - Minimal bench setup (example only)
Control signals only - motor power is external.

Use this setup for first checks and USB communication. No motors and no external driver power are connected.

```
USB Host
   |
   |  USB (data + 5 V logic)
   v
DUILIO F4
```

## 8.2 Typical motor driver connection
Figure 8-2 - Typical motor driver connection (example only)
Control signals only - motor power is external.

DUILIO F4 provides control signals to an external motor driver. Motor power is supplied externally and does not pass through DUILIO F4.

```
DUILIO F4                     External Motor Driver                  Motor Power
   |   PWM ----------------->  PWM input
   |   DIR ----------------->  DIR input
   |   ENABLE -------------->  ENABLE input
   |   GND ----------------->  GND reference
                                                               [External motor supply]
```

## 8.3 RC control setup
Figure 8-3 - RC control setup (example only)
Control signals only - motor power is external.

RC receiver outputs connect to the RC inputs with a shared 5 V and GND reference.
WARNING: RC +5 V is not a power input for the board.

```
RC Receiver
   |   PWM CH1..CH4 -------->  DUILIO F4 RC inputs
   |   +5 V ---------------->  RC +5 V (receiver supply)
   |   GND ----------------->  GND
```

## 8.4 Raspberry Pi integration
Figure 8-4 - Raspberry Pi integration (example only)
Control signals only - motor power is external.

Use a single 5 V power source for the stack or wired setup. Communication can be USB or serial.
WARNING: Avoid back-powering by ensuring only one 5 V source is active.

```
Single 5 V Source
        |
        +----> Raspberry Pi 5 V
        |
        +----> DUILIO F4 5 V (if configured)

Communication:
Raspberry Pi  <---- USB or Serial ---->  DUILIO F4
```

## 8.5 Common wiring mistakes
Figure 8-5 - Common wiring mistakes (example only)
Control signals only - motor power is external.

These examples highlight frequent errors that cause malfunction or damage.
WARNING: Each case can create unsafe current paths or undefined signal references.

```
1) Missing GND
DUILIO F4  ---- PWM/DIR ---->  Driver
           (no ground reference)

2) Motor power through DUILIO F4
Motor supply ---> DUILIO F4 ---> Motor/Driver

3) Multiple 5 V sources
USB 5 V  +  External 5 V  +  Pi 5 V (simultaneous)

4) Reversed servo/RC polarity
GND and +5 V swapped on RC/servo connector
```
