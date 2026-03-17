# 7. Function and Usage

This chapter describes how DUILIO F4 is intended to behave during normal installation and use.
It focuses on user-facing board behavior rather than internal firmware design details.

## 7.1 Board role in the system

DUILIO F4 sits between the command source and the external motor driver.
Its role is to:

- receive commands from the selected input path
- generate logic-level motion control signals
- manage supported I/O and field interfaces
- help maintain predictable startup and non-driving default behavior

It does not generate motor power and must always be used with external drivers suited to the application.

## 7.2 Typical control paths

Common public integration patterns include:

- RC receiver to DUILIO F4 to external driver
- host controller to DUILIO F4 to external driver
- Raspberry Pi to DUILIO F4 for higher-level logic with board-side real-time control
- multi-board RS485 systems with distributed nodes

Only one intended motion command source should be active at a time.

## 7.3 Driver command behavior

Depending on the driver type, DUILIO F4 can expose logic-level command signals such as:

- PWM
- DIR
- ENABLE
- BRAKE
- dual-PWM style outputs

These lines must be treated as control signals only.
The external driver remains responsible for power switching, current handling, and the final actuator behavior.

## 7.4 Startup behavior

At power-up, the board should be considered in a non-driving state until:

1. power is stable
2. the wiring has a valid reference and the intended source is active
3. the system enables motion intentionally

This startup discipline is necessary to avoid unwanted movement caused by floating references, unstable host startup, or ambiguous control ownership.

## 7.5 Normal operating expectations

During normal operation, the board is intended to provide:

- stable logic-level outputs for the connected driver
- repeatable behavior from the selected control path
- support for local and external I/O
- communication through the documented hardware interfaces

The final machine behavior still depends on firmware configuration, driver type, mechanics, and system integration quality.

## 7.6 Loss of command or fault conditions

Loss of valid command should be treated as an unsafe operating condition.
In practice, the integrator should expect the motion command path to be removed or fall back to a safe state defined by the complete system.

This includes cases such as:

- loss of host communication
- invalid input signals
- unstable power
- driver-side fault behavior

Final stop behavior must always be verified on the assembled machine.

## 7.7 Shutdown behavior

On shutdown or loss of power, control outputs should be expected to fall inactive.
The external driver and machine mechanics must be able to handle this state safely.

WARNING: Do not assume loss of board power equals safe machine stop unless the complete system has been designed and tested for that condition.

## 7.8 Integration guidance

For reliable field behavior:

- use a shared ground with every connected driver and host
- define a clear command ownership model
- validate driver response to ENABLE and BRAKE
- test startup and shutdown with the real load disconnected first
- review the total 5 V power budget before powering accessories from the board
