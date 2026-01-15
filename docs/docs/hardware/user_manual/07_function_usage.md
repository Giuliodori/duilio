# 7. Function and Usage
This chapter describes expected system-level behavior of DUILIO F4 when powered and connected, focusing on safe integration.

> NOTE: Power distribution and current limits (system-level)
> - Individual pin current ratings are maximum limits, not guarantees.
> - The sum of all output currents depends on the active power source.
> - When powered from VIN: total available 5 V current approx. 3 A continuous, 5 A peak (shared).
> - When powered ONLY from USB or Raspberry Pi GPIO: total available 5 V current < 0.8 A.
> - Exceeding the total budget may cause voltage drop, reset, or thermal shutdown.

## 7.1 Control signal logic
DUILIO F4 generates control signals for external motor drivers. It does not supply motor power and does not act as a power stage.
Electrical characteristics for control signals are specified in Chapter 6.

Motion control is implemented through PWM-based command signals. PWM encodes a requested speed or torque level as a duty cycle, while a separate direction line indicates the intended motion direction. Some drivers use combined DIR/PWM signaling; DUILIO F4 provides both PWM and direction-capable signals to support common interfaces.

At system level, these signals are intended to be treated as low-power logic commands. PWM, DIR, ENABLE, and BRAKE are logic-level signals only. The external driver is responsible for converting them into motor power. They must never be interpreted as power or safety-rated signals.

## 7.2 Enable, brake and safety behavior
ENABLE and BRAKE signals control whether a driver is permitted to move or is forced into a stop condition. ENABLE must be asserted for motion; BRAKE requests a forced stop or hold, depending on the driver.

The expected default is a safe state: outputs remain inactive until a valid control condition is established. This reduces unintended motion at power-up and after resets.

Explicit enabling is required before motion so the integrator can enforce system interlocks and startup checks. This ensures that motion only occurs after external conditions are verified safe.

## 7.3 Control source priority
DUILIO F4 can accept multiple control sources such as USB, RC inputs, and external host interfaces. Only one control source must be used for commanding motion at any time.

At system level, control selection is deterministic and predictable. If multiple sources are present, the system uses a defined priority so control does not oscillate between sources.

This behavior allows a clear hierarchy, for example manual RC takeover or an external host override, depending on the integration strategy.

## 7.4 Startup and shutdown behavior
At power-up, the board remains in a non-driving state while logic power stabilizes. Control outputs should be considered inactive until an explicit enable condition is met.

A controlled startup sequence consists of: stable logic power, valid control source, and explicit enabling. This sequence reduces unintended motion and ensures the external driver receives coherent command signals.

On shutdown or power loss, outputs return to a safe state. External drivers should be expected to stop or enter their own safe mode when control signals disappear.
WARNING: Do not rely on DUILIO F4 to maintain motion during power loss; external systems must handle safe stopping. System-level safety must be ensured by the external driver and mechanical design.

## 7.5 Fault and safe states
Loss of control signal should result in a safe state where motion commands are removed and drivers are disabled or braked, depending on the system configuration.

Loss of power results in all outputs dropping to inactive levels. External devices must be designed to fail safe in this condition.

Invalid or missing inputs should be treated as unsafe, and the system should prevent motion until inputs are valid again. This supports predictable behavior in noisy or unstable environments.
