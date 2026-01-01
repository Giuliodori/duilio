<p align="center">
  <img src="docs/images/logo_duilio.png" width="600">
</p>

<p align="center">
  <img src="docs/images/duilio_f4_top.png" width="45%">
  &nbsp;&nbsp;&nbsp;
  <img src="docs/images/duilio_f4_bottom.png" width="45%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/MCU-STM32F411-blue">
  <img src="https://img.shields.io/badge/Hardware-Prototype-orange">
  <img src="https://img.shields.io/badge/Bus-RS485%20%7C%20CAN-blueviolet">
  <img src="https://img.shields.io/badge/Raspberry%20Pi-Compatible-red">
  <img src="https://img.shields.io/badge/Maintained-Yes-brightgreen">
  <img src="https://img.shields.io/badge/License-MIT-green">
</p>

# DUILIO F4 — Motion Control Board
**Modular STM32F411-based motion and I/O control board for robotics and distributed systems**

**Duilio F4** is a modular control board designed for real-world robotic and mechatronic applications.

Instead of locking users into a specific power stage or motor topology,  
Duilio F4 allows you to **choose the most suitable external motor driver** and adapt the control logic accordingly.

It can be used:
- as a **standalone controller**
- as an **expansion board for Raspberry Pi**
- as part of a **distributed multi-board system** using a robust communication bus

The same board can scale from simple projects to complex machines with many motors and peripherals.

---

## Status

- **Hardware**: Prototype (first production run in progress)
- **Firmware**: Under active development
- **Tools**: Planned / early development

Documentation and software will be published progressively as the hardware is validated.

---

## Core concepts

Duilio F4 is built around a few key design principles:

- **Driver-agnostic architecture**  
- **Scalable multi-board systems**
- **Robust and deterministic communication**
- **Fail-safe oriented design**
- **Profile-based configuration instead of custom code**

This approach allows the same hardware and firmware architecture to be reused across very different applications.

---

## What Duilio F4 can do

### Standalone operation or host computer integration

Duilio F4 can operate in different system configurations:

- as a **standalone controller**, driven by RC receivers, potentiometers or local inputs
- as a **USB-controlled device**, connected to a host computer
- as a **Raspberry Pi HAT**, directly mounted on the GPIO header

When used as a USB-controlled device, Duilio F4 can be driven by:
- Raspberry Pi
- single-board computers such as Orange Pi, Rock Pi, Jetson Nano
- standard PCs or industrial computers

In these configurations, Duilio F4 handles real-time motion control and I/O,
while the host system provides high-level logic, user interfaces or networking.

---

### Motor control flexibility
Duilio F4 supports a wide range of external motor drivers, including:

- DC motors (brushed)
- BLDC motor drivers
- common **PWM / DIR** drivers
- industrial drivers using enable, direction and speed signals

Typical control modes include:
- speed control and limiting
- position control
- mixed configurations (different modes on different motors)

Duilio F4 does not implement a single fixed motor control strategy.

Each external driver is associated with a **control profile**, defining:
- signal types (PWM, DIR, ENABLE, analog, serial)
- scaling and operating limits
- safety and fail-safe behavior

This allows the same firmware architecture to be reused across very different projects.

---
### Power supply and system integration

Duilio F4 is designed to greatly simplify power distribution in robotic and mechatronic systems.

The board supports multiple power input scenarios:

- **Wide input supply (VIN)** from **6 V to 43 V**
- **5 V supply from USB**
- **5 V supply from a Raspberry Pi** when used as a HAT
- 
The board automatically manages the active power source,
preventing back-feeding between VIN, USB and Raspberry Pi supplies.

When powered from the VIN input, Duilio F4 provides regulated power to the rest of the system,
including the host computer and peripherals.

#### Raspberry Pi power support
When used together with a Raspberry Pi, Duilio F4 can:
- automatically **power the Raspberry Pi through the GPIO header**
- supply up to **5.1 V at 5 A**, suitable for Raspberry Pi and connected peripherals
- avoid the need for external power adapters or additional wiring

If the Raspberry Pi is already powered independently, Duilio F4 adapts accordingly
without forcing a single power topology.

#### RC servo power distribution
When powered from VIN, Duilio F4 can also supply power to **RC servo outputs**:

- regulated servo supply suitable for small RC servos and low-power actuators
- **PTC resettable fuse (2 A)** for protection against overloads or short circuits
- direct control of small servos without additional external power modules

This allows compact and clean system designs, especially in mobile or embedded applications.

#### Protection and robustness
To ensure reliable operation in real-world environments, Duilio F4 includes:

- reverse polarity protection
- transient suppression (**TVS diodes**)
- **ESD protection** on sensitive interfaces
- protection diodes to isolate power domains

These measures protect both the board and connected peripherals
in electrically noisy environments, such as systems with motor drivers and switching regulators.

---

### Multi-board systems and broadcast control
Multiple Duilio boards can be connected together using a **robust communication bus**.

- many boards can operate simultaneously
- commands can be sent in **broadcast mode**
- each board can return telemetry data
- a single controller can manage multiple motors across the system

This architecture allows Duilio F4 to scale from a single-board prototype  
to complex distributed machines without changing the overall software design.

---

### Safety and reliability
Duilio F4 is designed for real-world environments and includes:

- configurable **failsafe mechanisms**
- safe motor shutdown on communication loss
- predictable startup behavior
- clear separation between control logic and power electronics

---

### Inputs and peripherals
Supported peripherals include:

- RC radio receivers
- ultrasonic sonar sensors
- standard **RC servo outputs**
- digital and analog inputs for external sensors

---

## Typical use cases

Duilio F4 is suitable for a wide range of applications:

- **Mobile robots and autonomous platforms**  
  Coordinated control of motors, sensors and safety inputs.

- **Remote-controlled machines**  
  Integration with RC receivers, PWM/DIR motor drivers and servos.

- **Multi-axis systems**  
  Speed or position control of several motors, even across multiple boards.

- **Distributed robotic systems**  
  Multiple Duilio boards connected on a robust bus with broadcast commands.

- **Raspberry Pi based controllers**  
  Offloading real-time motion control and I/O handling from the main computer.

- **Prototyping and custom machines**  
  A flexible platform for rapid development and iteration.

---

## Duilio Tools (configuration software)

**Duilio Tools** is the official configuration and debugging software.

It allows:
- board configuration with a few clicks
- parameter tuning without writing code
- real-time monitoring and diagnostics

Duilio Tools is designed so that **even users without specific programming knowledge**
can configure and use the board effectively.

The board ships with a standard firmware but can be fully customized.

Advanced users remain free to bypass Duilio Tools and work directly with the firmware.

---

## What Duilio F4 is not

- It is **not** a high-power motor driver
- It does **not** include motor power stages
- It does **not** impose a single control architecture

Duilio F4 is designed to sit *between* control sources and power electronics,
providing motion logic, safety, scaling and coordination.

It can be used in both simple and complex configurations.

---

## Communication robustness and scalability

Duilio F4 is designed to operate reliably in electrically noisy environments,
such as systems with motor drivers, switching power supplies and long cable runs.

Supported communication options include:

- **UART or USB** for local or point-to-point connections
- **RS485** for long-distance, noise-resistant communication
- **RS485 multi-drop bus** for distributed multi-board systems

When multiple boards are connected on an RS485 bus:
- commands can be broadcast
- telemetry can be collected from each node
- deterministic and low-latency communication is achievable
- the system remains stable even in harsh EMI environments

This makes Duilio F4 suitable for machines where reliability and predictability
are more important than raw bandwidth.

---

## Planned repository structure

The repository is organized to support the Duilio platform as it evolves,
from early prototypes to validated hardware and software releases.

```text
duilio/
├── hardware/
│   └── duilio-f4/
│       ├── README.md            # Board overview and specifications
│       ├── pinout/              # Functional pin mapping
│       ├── images/              # Board images and renders
│       └── revisions/           # Hardware revisions and notes
│
├── firmware/
│   └── duilio-f4/
│       ├── README.md            # Firmware overview and build notes
│       ├── src/
│       ├── include/
│       └── profiles/            # Driver and control profiles
│
├── tools/
│   └── duilio-tools/
│       ├── README.md            # Configuration and debug tools
│       └── src/
│
└── docs/
    ├── getting-started/
    ├── communication/
    ├── drivers/
    ├── safety/
    └── images/


---

© 2026 Fabio Giuliodori — Duilio Project

This structure will evolve as the project grows.


