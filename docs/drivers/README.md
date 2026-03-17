# Driver Examples

DUILIO F4 is designed to work with external motor drivers.
The board provides logic-level control and supervision signals; it does not provide motor power.

## Public guidance

Use the simplified diagrams in the hardware manual for common driver classes:

- PWM and DIR drivers
- dual-PWM / servo-style drivers
- closed-loop configurations with external feedback devices

## Integration rule

Before connecting any driver, verify:

- signal voltage compatibility
- shared ground reference
- external motor power routing
- expected behavior of ENABLE and BRAKE lines

See [../hardware/08_connection_diagrams.md](../hardware/08_connection_diagrams.md) for example wiring concepts.
