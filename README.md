z<p align="center">
  <img src="docs/images/logo_duilio.png" width="600">
</p>

<div align="center">
  <img src="docs/images/duilio_f4_top.png"
       style="display:block; margin:auto; width:85%;">
</div>


<p align="center">
  <img src="https://img.shields.io/badge/MCU-STM32F411-blue">
  <img src="https://img.shields.io/badge/Hardware-Prototype-orange">
  <img src="https://img.shields.io/badge/Bus-RS485%20%7C%20CAN-blueviolet">
  <img src="https://img.shields.io/badge/Raspberry%20Pi-Compatible-red">
  <img src="https://img.shields.io/badge/Maintained-Yes-brightgreen">
  <img src="https://img.shields.io/badge/License-MIT-green">
</p>

# DUILIO F4 — Motion Control Board
**A purpose-built motion and I/O control board for real-world machines**

**Duilio F4** is a **ready-to-use motion control board**, designed to reliably command external motor drivers
in robotic and mechatronic systems.

It is **not a generic development board**.
Duilio F4 combines **robust hardware**, **pre-developed firmware** and a dedicated configuration tool
to control motors and I/O without writing application code.

Instead of forcing a specific motor topology or power stage,
Duilio F4 lets you **select the most suitable external motor driver**
and adapts the control logic through predefined profiles.

Configuration and customization are handled through **Duilio Tools**:
a dedicated software that allows users to:
- configure the board with a few clicks
- adapt it to different drivers and machines
- perform advanced graphical debugging
- work **without writing a single line of code**

It can be used:
- as a **standalone motion controller**
- as a **USB-controlled device** driven by a PC or single-board computer
- as a **Raspberry Pi HAT**
- as part of a **distributed multi-board system** using a robust communication bus

Duilio F4 is designed for engineers and makers who want to build machines,
not spend weeks writing low-level control code.
It is designed for system development, prototyping
and integration into custom machines and robotic platforms.


---

## Status

- **Hardware**: Third-generation prototype, with multiple production iterations completed
- **Firmware**: Actively developed and tested on real hardware
- **Duilio Tools**: Operational and in active use, currently being adapted to the new 64-pin STM32 platform

Documentation and software are being published progressively
as the current hardware validation phase advances.

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

Duilio F4 is designed to **turn simple, robust and cost-effective motor drivers
into fully featured motion control systems**.

Rather than implementing motor power stages directly, Duilio F4 adds intelligence,
coordination and safety on top of widely available external drivers.

It supports a broad range of driver interfaces, including:

- DC motor drivers (brushed)
- BLDC motor drivers
- **PWM / DIR** drivers
- **PWM forward / PWM reverse (PWMF / PWMR)** drivers
- analog speed + direction drivers
- industrial drivers using enable, direction and speed signals

Thanks to this approach, inexpensive and rugged drivers can be used
in applications that normally require far more complex controllers.

#### Advanced motion features

Depending on the selected control profile, Duilio F4 can provide:

- acceleration and deceleration ramps
- speed limiting and soft limits
- motion mixing (e.g. differential drive, coordinated axes)
- position control and positioning logic
- configurable safety behaviors and interlocks

Position feedback can be handled using multiple strategies, including:
- relative position tracking
- absolute position sensing
- external encoders or sensors
- hybrid approaches combining multiple feedback sources

#### Profile-based control architecture

Duilio F4 does not rely on a single fixed motor control strategy.

Each external driver is associated with a **control profile** that defines:
- signal interfaces (PWM, DIR, ENABLE, analog, serial)
- scaling, limits and dynamic behavior
- acceleration profiles and motion constraints
- safety rules and fail-safe actions
- optional position and telemetry handling

This allows the same firmware and hardware platform to adapt to
very different machines and driver types,
while maintaining predictable behavior and robust safety logic.

As a result, Duilio F4 can scale from simple motor control tasks
to complex multi-axis and coordinated motion systems
without changing the overall architecture.

### Driver compatibility

Duilio F4 is designed to work with a wide range of **simple, robust and widely available motor drivers**.

Rather than targeting a limited set of proprietary controllers,
Duilio F4 adapts to common control interfaces used by many DC and BLDC drivers.

The following driver types are **supported or supportable**, depending on the selected control profile
and available feedback signals.

#### Supported driver interface types

**Digital control drivers**
- PWM + DIR
- PWM forward / PWM reverse (PWMF / PWMR)
- ENABLE + DIR + PWM
- STEP + DIR (speed-based or position-based usage)
- dual-PWM speed control

**Analog control drivers**
- analog speed input (0–5 V, 0–10 V via external conditioning)
- analog speed + direction
- mixed analog/digital interfaces

**RC-style drivers**
- standard RC PWM input (servo-style pulse width)
- electronic speed controllers (ESC) with forward / reverse support

**Serial or protocol-based drivers**
- simple serial-controlled drivers
- custom or proprietary serial protocols (profile-dependent)

---

#### Typical compatible driver categories

Duilio F4 can be used with:

- low-cost DC motor driver modules
- industrial DC motor controllers
- brushed motor H-bridge drivers
- BLDC motor drivers with external speed/direction inputs
- ESCs accepting RC PWM signals
- custom motor drivers exposing basic control signals

In many cases, drivers originally intended for manual or open-loop control
can be upgraded into closed-loop or coordinated systems
by combining them with Duilio F4 motion logic and feedback handling.

---

#### Notes on compatibility

- Duilio F4 does **not** require drivers to implement complex protocols
- drivers only need to expose basic speed, direction or enable signals
- feedback signals (encoders, sensors, limit switches) can be added externally
- compatibility is defined through **control profiles**, not hardcoded driver models

This approach allows Duilio F4 to remain flexible,
future-proof and adaptable to new driver types as they become available.

---

### Power supply and system integration

Duilio F4 is designed to greatly simplify power distribution in robotic and mechatronic systems.

The board supports multiple power input scenarios:

- **Wide input supply (VIN)** from **6 V to 43 V**
- **5 V supply from USB**
- **5 V supply from a Raspberry Pi** when used as a HAT

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
## Real-world inspiration

Duilio F4 is the result of hands-on experience gained while building
real machines and robotic platforms.

Some of these projects are documented here:

▶️ **Remote-controlled mower 2wd** https://youtu.be/Uh7IwvmYxhc  

▶️ **Remote-controlled mower 4wd** https://youtu.be/W-mF7ZH8-0U

▶️ **Trike** https://youtu.be/o_xk7uZkcA0

▶️ **Stroller** https://youtu.be/8yrex-ifpPg

▶️ **Shaker** https://youtu.be/M_itfUgND1k


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
├── docs/
│   ├── getting-started/
│   ├── communication/
│   ├── drivers/
│   ├── safety/
│   └── images/
│
├── CHANGELOG.md                 # Project changelog
├── CONTRIBUTING.md              # Contribution guidelines
├── SECURITY.md                  # Security and safety policy
└── .github/                     # Issue templates and workflows

This structure will evolve as the project grows.
```
## Project governance

See also:
- [CONTRIBUTING.md](./CONTRIBUTING.md) — how to contribute
- [SECURITY.md](./SECURITY.md) — responsible disclosure and safety
- [CHANGELOG.md](./CHANGELOG.md) — project history


## Collaboration

Open to collaboration supporting the next development phases
of the Duilio platform.

---
© 2026 Fabio Giuliodori — Duilio Project




