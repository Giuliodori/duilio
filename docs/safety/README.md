# Safety Notes

DUILIO F4 is a control board, not a motor power stage and not a safety-rated device.

## Core safety points

- Motor power must remain external to DUILIO F4.
- Functional safety must be implemented at system level.
- Avoid multiple active 5 V sources unless power flow is explicitly designed.
- Use a shared ground with every connected driver, host, and sensor.
- Perform first tests with the mechanical load removed or secured.

Read the full safety chapter here:

- [Hardware safety precautions](../hardware/03_safety.md)
