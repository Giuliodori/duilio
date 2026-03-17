# 3. Safety Precautions

This chapter summarizes the main safety-related rules for installing and using DUILIO F4 in a real machine or test setup.

## 3.1 Scope of the board

DUILIO F4 is a control board.
It is not a motor power stage, not a complete machine safety system, and not a safety-certified controller.

The following functions remain external responsibilities:

- motor power switching
- emergency stop strategy
- actuator braking behavior
- mechanical hazard mitigation
- enclosure, wiring, and system-level protection

## 3.2 Electrical and functional safety

Electrical safety concerns correct voltage, current, polarity, grounding, insulation, and protection against transients or shorts.
Functional safety concerns how the machine behaves when something goes wrong.

DUILIO F4 helps with predictable control and safe-state logic, but the final machine safety depends on:

- the external driver
- the power architecture
- the mechanical system
- the integrator's wiring and commissioning choices

## 3.3 Main electrical hazards

The most common electrical hazards during integration are:

- reverse polarity or incorrect VIN connection
- back-powering through USB, Raspberry Pi, or external 5 V
- motor current mistakenly routed through the board
- missing common ground between board and driver
- overloaded 5 V auxiliary rail
- probing or modifying jumpers while powered

> NOTE: Power distribution and current limits (system-level)
> - Individual pin current ratings are maximum limits, not guarantees.
> - The sum of all output currents depends on the active power source.
> - When powered from VIN: total available 5 V current approx. 3 A continuous, 5 A peak (shared).
> - When powered ONLY from USB or Raspberry Pi GPIO: total available 5 V current < 0.8 A.
> - Exceeding the total budget may cause voltage drop, reset, or thermal shutdown.

## 3.4 Power and back-powering precautions

Use only one intended 5 V source at a time unless the complete power tree has been explicitly designed for multiple paths.

Back-powering can occur when:

- USB is connected while another 5 V source is active
- Raspberry Pi 5 V is linked without a defined power direction
- external logic injects power into I/O or accessory rails

This can cause uncontrolled startup, unstable logic behavior, or damage to connected equipment.

WARNING: Before connecting USB, Raspberry Pi, or external 5 V, review the selected power scenario in Chapter 4.

## 3.5 Motion hazards

Motor systems can move unexpectedly because of:

- configuration errors
- signal wiring mistakes
- noise or unstable references
- incorrect driver interpretation of ENABLE, BRAKE, or PWM lines
- loss and restoration of power

During first tests:

- remove or decouple the mechanical load when possible
- secure the machine against unintended movement
- keep people clear of the motion area
- validate one subsystem at a time

## 3.6 Safe inputs and operating discipline

The board includes local input lines intended for controlled user interaction and safe-state related logic, but these do not replace a machine emergency-stop chain.

Treat local safe inputs as part of the control architecture, not as a certified personnel safety function.

If the machine can create injury, implement independent hardware-level safety measures outside the board.

## 3.7 Commissioning checklist

Before first power-up:

- verify VIN polarity and voltage
- inspect for shorts, damaged insulation, and loose strands
- verify external driver wiring before enabling outputs
- confirm common ground between DUILIO F4 and every connected driver or host
- use a current-limited supply for the first validation step
- keep motors or high-risk loads disconnected when possible
- confirm the intended 5 V power direction
- ensure an accessible power cutoff is available
- mount the board securely and provide strain relief

## 3.8 Service precautions

Use SWD, boot configuration, and measurement points only in controlled service conditions.

Do not:

- change jumpers while powered
- short adjacent pins during measurement
- assume service headers are protected against misuse
- perform live modifications near exposed power paths without proper precautions
