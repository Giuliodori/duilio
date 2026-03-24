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

DUILIO F4 is a motion control board built for real machines, mobile robots, and custom electromechanical systems.
It brings together deterministic board-level control, practical field I/O, and a wiring model designed for external motor drivers, not toy demos.

The goal is simple: make robust motion systems easier to build.
Instead of rewriting the same low-level glue for every machine, DUILIO F4 provides a solid control layer between the host logic and the power electronics.

<div align="center">
  <img src="docs/images/duilio_f4_top.png" width="45%" alt="Duilio F4 top view">
  &nbsp;&nbsp;&nbsp;
  <img src="docs/images/duilio_f4_bottom.png" width="45%" alt="Duilio F4 bottom view">
</div>


## Why DUILIO F4

- Real-time board-level control on STM32F411
- Two motor-control axes per board
- 4 RC input and 4 RC output support per board
- USB, UART, I2C, and RS485 integration
- Separate 5 V and 3.3 V logic domains where required
- Designed for external motor drivers, sensors, and host controllers

## Typical applications

- RC vehicles and work machines
- Raspberry Pi based robotic platforms
- Dual-axis motion systems
- Custom servo-like systems 
- Bench validation and field prototyping

## Documentation

- [Hardware Manual](docs/hardware/00_front_matter.md)
- [Getting Started](docs/getting-started/README.md)
- [Driver Examples](docs/drivers/README.md)
- [Communication Overview](docs/communication/README.md)
- [Safety Notes](docs/safety/README.md)
- [Software Download](software-download/README.md)

## Duilio Tools

Duilio Tools is the official Windows utility for configuring and diagnosing DUILIO F4.
It is intended to make setup and validation accessible without exposing the private development tooling.

<div align="left">
  <img src="docs/images/duilio-tools_2.png" style="display:block; margin:auto; width:100%;" alt="Duilio Tools configuration view">
</div>
<div align="left">
  <img src="docs/images/duilio-tools_1.png" style="display:block; margin:auto; width:95%;" alt="Duilio Tools diagnostics view">
</div>

Installer and quick Windows instructions are available in [software-download/README.md](software-download/README.md).

## Scope

This repository includes:

- hardware manual and public technical characteristics
- simplified wiring examples and connector reference
- software download and end-user instructions

It does not publish the full private hardware development files, production package, or private firmware source tree.

## Contact

- info@duilio.cc
- https://duilio.cc

## License

See [LICENSE](LICENSE).

Licensing questions, commercial use, and redistribution requests: `info@duilio.cc`.

Copyright (c) 2026 Fabio Giuliodori.
