<p align="center">
  <img src="docs/images/logo_duilio.png" width="600">
</p>

<div align="center">
  <img src="docs/images/duilio_f4_top.png" style="display:block; margin:auto; width:100%;">
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
The wheel is already there.
**Duilio turns motor drivers into real motion control.**

In robotics and mechatronics, the real challenge is not driving motors,
but turning simple motor drivers into reliable, coordinated and safe motion systems.

Duilio F4 solves this problem by **removing the need to reinvent control logic**:
it transforms basic, rugged or industrial motor drivers into advanced motion controllers
**without writing custom control firmware**.

Duilio F4 is a **ready-to-use motion control board** that sits between
control sources (RC receivers, PCs, Raspberry Pi and other SBCs)
and **external motor drivers**, adding intelligence, coordination and safety.

It is **not a generic development board**.
Duilio F4 combines robust hardware, pre-developed firmware
and a dedicated configuration tool (**Duilio Tools**)
to configure motors and I/O **without writing application code**.

Instead of forcing a specific motor topology or power stage,
Duilio F4 lets you choose the most suitable external driver
(PWM/DIR, analog, RC-style or industrial interfaces)
and adapts the control behavior through **predefined control profiles**.

This allows inexpensive, rugged or industrial drivers
to behave like fully featured motion controllers,
with acceleration ramps, limits, mixers, positioning logic and failsafe handling.


---

## Status
- **Hardware**: Third-generation prototype, multiple production iterations completed
- **Firmware**: Actively developed and tested on real hardware
- **Duilio Tools**: Operational and in active use, currently being adapted to the new 64-pin STM32 platform

Documentation and software are published progressively as hardware validation advances.

---

## Core design principles
- **Driver-agnostic architecture**
- **Profile-based configuration (instead of custom code)**
- **Robust and deterministic communication**
- **Fail-safe oriented behavior**
- **Scalable multi-board systems**

---

## System architecture
Duilio F4 can be controlled by:
- Raspberry Pi
- single-board computers (Orange Pi, Rock Pi, Jetson Nano, …)
- standard PCs or industrial computers

In host-controlled configurations, Duilio F4 handles real-time motion control and I/O, while the host provides high-level logic, UI, or networking.

---

## Motor control
Duilio F4 is designed to turn **simple, robust and cost-effective drivers** into **fully featured motion control systems**.

### Supported / supportable driver interfaces
- **PWM / DIR**
- **PWM forward / PWM reverse (PWMF / PWMR)**
- **ENABLE + DIR + PWM**
- **dual-PWM speed control**
- **STEP / DIR** (speed-based or position-based usage)
- **analog speed** (0–5V)
- **analog speed + direction**
- **RC-style PWM** (servo pulses / ESCs)
- **serial / protocol-based drivers** (profile-dependent)

### Motion features (profile-dependent)
- acceleration / deceleration ramps
- speed limiting and soft limits
- motion mixing (e.g. differential drive, coordinated axes)
- position control and positioning logic
- safety behaviors, interlocks and failsafe actions

### Position feedback (profile-dependent)
- relative position tracking
- absolute position sensing
- external encoders or sensors
- hybrid approaches (combined sources)

All behavior is defined through **control profiles** (interfaces, scaling, limits, dynamics, safety, optional telemetry/feedback handling).

---

## Power supply and system integration
Duilio F4 simplifies power distribution in robotic systems.

### Power inputs
- **VIN**: **6 V to 43 V**
- **5 V from USB**
- **5 V from Raspberry Pi** (HAT mode)

The board automatically manages active sources and prevents back-feeding between VIN, USB.

### Raspberry Pi power support
- powers Raspberry Pi via GPIO
- up to **5.1 V / 5 A**
- reduces external adapters and wiring

### RC servo power distribution
- regulated servo supply for small servos/actuators
- **PTC resettable fuse (2 A)**
- direct servo control without external power modules (for small loads)

### Protection and robustness
- TVS transient suppression
- ESD protection on sensitive interfaces
- isolation/protection diodes between power domains

Designed for electrically noisy environments (motor drivers, switching regulators, long cables).

---

## Communication robustness and scalability
Supported communication options:
- **UART**
- **USB**
- **RS485** (multi-drop)

In RS485 multi-board systems:
- broadcast commands
- per-node telemetry return
- deterministic, low-latency behavior
- stable operation in harsh EMI environments

---

## Typical use cases
- mobile robots and autonomous platforms
- remote-controlled machines
- multi-axis and coordinated motion systems
- distributed robotic systems
- Raspberry Pi–based controllers
- rapid prototyping of custom machines

---

## Real-world inspiration
Duilio F4 is the result of hands-on experience gained while building real machines and robotic platforms.

Some of these projects are documented here:
- ▶️ **Remote-controlled mower (2WD)** — https://youtu.be/Uh7IwvmYxhc  
- ▶️ **Remote-controlled mower (4WD)** — https://youtu.be/W-mF7ZH8-0U  
- ▶️ **Trike** — https://youtu.be/o_xk7uZkcA0  
- ▶️ **Stroller** — https://youtu.be/8yrex-ifpPg  
- ▶️ **Shaker** — https://youtu.be/M_itfUgND1k  

---

## Duilio Tools
**Duilio Tools** is the official configuration and debugging software.

It provides:
- guided board configuration
- parameter tuning without writing firmware code
- real-time monitoring and diagnostics
- advanced graphical debugging

<div align="left">
  <img src="docs/images/duilio-tools_2.png" style="display:block; margin:auto; width:100%;">
</div>
<div align="left">
  <img src="docs/images/duilio-tools_1.png" style="display:block; margin:auto; width:95%;">
</div>

Duilio Tools is designed so that **even users without specific programming knowledge** can configure and use the board effectively.
Advanced users remain free to bypass the tool and work directly with the firmware.

---

## What Duilio F4 is not
- not a high-power motor driver
- no integrated motor power stages
- no fixed control architecture

Duilio F4 sits between control sources and power electronics, providing motion logic, safety, scaling and coordination.

---

## Planned repository structure
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
│       └── profiles/            # Driver control profiles
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




