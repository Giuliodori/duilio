# Getting Started

This section is the fast entry point for a new DUILIO F4 user.

## Minimum path to first power-up

1. Read the safety notes in [../safety/README.md](../safety/README.md).
2. Verify the supply strategy in [../hardware/04_power_system.md](../hardware/04_power_system.md).
3. Identify the correct connector in [../hardware/06_connectors_pinout.md](../hardware/06_connectors_pinout.md).
4. Start from a simplified wiring example in [../hardware/08_connection_diagrams.md](../hardware/08_connection_diagrams.md).
5. Configure the board with Duilio Tools as described in [../../tools/README.md](../../tools/README.md).

## First integration recommendations

- Start without mechanical load whenever possible.
- Use only one intended 5 V source at a time.
- Keep motor power external to DUILIO F4.
- Establish a common ground with each external driver and host.
- Enable motion only after confirming wiring and safe-state behavior.
