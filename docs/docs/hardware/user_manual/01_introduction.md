# 1. Introduction

## 1.1 What is DUILIO F4
DUILIO F4 is a modular motion control board based on STM32, designed to act as the central interface between control logic and external motor drivers. It supports multiple control sources, including RC receivers, USB, and Raspberry Pi. The board separates 5 V and 3.3 V logic domains to accommodate mixed-voltage peripherals and improve system integration.

## 1.2 Intended use
DUILIO F4 is intended for technical development and integration in:
- Prototyping and validation benches.
- Embedded systems requiring deterministic motor control interfaces.
- Robotics and motion control platforms.

## 1.3 What DUILIO F4 is not
DUILIO F4 is not a high-power motor driver and must be paired with appropriate external power stages. It is not a consumer plug-and-play product and is not designed for general-purpose end users. It is also not designed or certified for safety-critical environments that require functional safety compliance.

## 1.4 Typical system architectures
Typical system architectures include:
- STM32 standalone: the onboard MCU manages I/O and motor interfaces without external hosts.
- STM32 + Raspberry Pi: a Raspberry Pi provides high-level control while STM32 handles real-time motion tasks.
- RC + external drivers: RC input commands external motor drivers through DUILIO F4 interfaces.
