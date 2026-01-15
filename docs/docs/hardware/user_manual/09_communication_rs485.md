# 9. Communication Interfaces
This chapter describes the hardware communication interfaces available on DUILIO F4. Protocol details are intentionally excluded.

## 9.1 RS485 interface overview
RS485 provides a robust differential interface intended for multi-drop communication between multiple DUILIO F4 boards and a host system.
At hardware level, the bus supports multiple nodes sharing a single pair, with each node connected in parallel.
Differential signaling improves noise immunity in electrically noisy environments.
No protocol definition is provided in this chapter.

## 9.2 RS485 hardware integration guidelines
Use a twisted pair for the RS485 differential lines to maintain signal integrity.
A common ground between all connected devices is required to keep the differential reference within valid limits.
RS485 lines are differential signals only; do not apply external voltage. Termination and biasing depend on the system topology.

Termination and biasing are required at the system level. Apply them according to network topology and cable length, without relying on default assumptions.
Typical wiring mistakes include missing ground reference, star wiring with long stubs, and inconsistent termination.

## 9.3 I2C interface overview
DUILIO F4 provides I2C connectors for external sensors and peripherals.
The interface is intended for short-distance, board-level communication with compatible devices.
I2C signals are logic-level and require compatible voltage levels on connected devices.

## 9.4 I2C hardware integration guidelines
I2C is a shared bus; all devices connect in parallel and share the same clock and data lines.
Pull-up resistors are required on the bus; ensure they exist in the system and avoid duplicating excessive pull-ups.
Keep cable lengths short and avoid routing near high-current wiring to reduce noise and signal distortion.
A shared ground reference between DUILIO F4 and I2C devices is mandatory.

## 9.5 Protocol status
This manual covers the hardware interface only. Protocol details, addressing, and timing are defined in firmware documentation and integration notes.
