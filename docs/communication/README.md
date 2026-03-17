# Communication Overview

DUILIO F4 can be integrated through different communication paths depending on the system architecture.

## Publicly documented interfaces

- USB for configuration and service workflows
- UART for host integration
- RS485 for multi-node hardware topologies
- I2C for supported peripheral and sensor connections

## Scope of this public section

This section documents the hardware-facing integration view only.
Detailed private protocol implementation notes are not published in this repository.

For interface constraints and wiring rules, see [../hardware/09_communication_rs485.md](../hardware/09_communication_rs485.md).
