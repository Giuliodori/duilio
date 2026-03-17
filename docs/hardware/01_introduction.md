# 1. Introduction

## 1.1 What is DUILIO F4
DUILIO F4 is a motion control board based on STM32F411.
It acts as the interface layer between high-level control logic and external motor drivers, handling real-time signals, field wiring, and board-level control functions.

The board is intended for systems where deterministic I/O behavior, safe startup, and practical machine integration matter more than exposing raw MCU pins.
Typical control sources include RC receivers, USB-connected PCs, Raspberry Pi, and distributed RS485 systems.

## 1.2 Intended use
DUILIO F4 is intended for technical development and integration in:

- robots and mobile platforms
- RC-controlled machines and custom vehicles
- actuator control systems with external motor drivers
- validation benches and integration prototypes
- Raspberry Pi based control architectures

## 1.3 What DUILIO F4 is not
DUILIO F4 is not a high-power motor driver and must always be paired with suitable external power stages.
It is not a complete safety system, not a functional-safety-certified controller, and not a consumer plug-and-play motor product.
Motor power, emergency stop strategy, and machine-level protections remain external responsibilities.

## 1.4 Typical system architectures
Typical system architectures include:

- Standalone board plus external drivers: DUILIO F4 handles motion I/O locally.
- DUILIO F4 plus Raspberry Pi: the host runs the application logic while DUILIO F4 handles deterministic real-time control.
- RC receiver plus external drivers: RC inputs command the board directly for manual or machine-control scenarios.
- Multi-node RS485 installation: multiple boards are used as distributed motion and I/O nodes.
