<p align="center">
  <img src="docs/images/logo_duilio.svg" width="320" alt="Duilio logo">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/MCU-STM32F411-blue" alt="MCU STM32F411">
  <img src="https://img.shields.io/badge/Hardware-Validation%20Stage-orange" alt="Hardware validation stage">
  <img src="https://img.shields.io/badge/Bus-RS485-blueviolet" alt="RS485 bus">
  <img src="https://img.shields.io/badge/Host-Raspberry%20Pi%20%7C%20USB-red" alt="Host Raspberry Pi and USB">
  <img src="https://img.shields.io/badge/Tools-Windows%20Executable-brightgreen" alt="Windows executable available">
</p>

# DUILIO F4

DUILIO F4 is an STM32-based motion control board for real machines, mobile robots, and custom actuators.
It sits between the high-level controller and the external motor drivers, handling real-time I/O, motion logic, and safe-state behavior on the board.

This public repository is a product-facing documentation repository.
It contains the user-facing hardware manual, simplified connection diagrams, and software usage notes.
It does not contain the complete private hardware design files, production package, or firmware source tree.

## What this repository includes

- Public hardware manual and technical characteristics
- Simplified wiring examples for common integration scenarios
- Connector and pinout reference for end users and integrators
- Public-facing notes for Duilio Tools and software distribution

## What this repository does not include

- Full KiCad project and private hardware development files
- Detailed production data, internal compliance files, or business documents
- Private firmware source code and manufacturing tooling
- Provisioning, licensing, or release-internal utilities

## Documentation map

- [Hardware Manual](docs/hardware/00_front_matter.md)
- [Getting Started](docs/getting-started/README.md)
- [Driver Examples](docs/drivers/README.md)
- [Communication Overview](docs/communication/README.md)
- [Safety Notes](docs/safety/README.md)
- [Software Download](software-download/README.md)

## Hardware at a glance

<div align="center">
  <img src="docs/images/duilio_f4_top.png" width="45%" alt="Duilio F4 top view">
  &nbsp;&nbsp;&nbsp;
  <img src="docs/images/duilio_f4_bottom.png" width="45%" alt="Duilio F4 bottom view">
</div>

- STM32F411 control core
- Two motor-control axes per board
- RC input and RC output support
- USB, UART, I2C, and RS485 integration
- Separate 5 V and 3.3 V logic domains where required
- Designed to work with external motor drivers, not to replace them

## Example use cases

- RC vehicles and work machines
- Raspberry Pi based robotic platforms
- Dual-axis motion control systems
- Custom servo-like systems built from motor plus external driver
- Bench validation and field prototyping

## Duilio Tools

Duilio Tools is the official configuration and diagnostics utility for DUILIO F4.
The public distribution path is documented in [software-download/README.md](software-download/README.md).

<div align="left">
  <img src="docs/images/duilio-tools_2.png" style="display:block; margin:auto; width:100%;" alt="Duilio Tools configuration view">
</div>
<div align="left">
  <img src="docs/images/duilio-tools_1.png" style="display:block; margin:auto; width:95%;" alt="Duilio Tools diagnostics view">
</div>

## Contact

- info@duilio.cc
- https://duilio.cc

## License

See [LICENSE](LICENSE).

Licensing questions, commercial use, and redistribution requests: `info@duilio.cc`.

Copyright (c) 2026 Fabio Giuliodori.
