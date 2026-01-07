<p align="center">
  <img src="docs/images/logo_duilio.png" width="600">
</p>

<div align="center">
  <img src="docs/images/duilio_f4_top.png" style="display:block; margin:auto; width:95%;">
</div>

<p align="center">
  <img src="https://img.shields.io/badge/MCU-STM32F411-blue">
  <img src="https://img.shields.io/badge/Hardware-Prototype-orange">
  <img src="https://img.shields.io/badge/Bus-RS485-blueviolet">
  <img src="https://img.shields.io/badge/Raspberry%20Pi-Compatible-red">
  <img src="https://img.shields.io/badge/Maintained-Yes-brightgreen">
  <img src="https://img.shields.io/badge/License-MIT-green">
</p>

# DUILIO F4 — Motion Control Board

***The wheel is already made, Duilio makes it move the right way.***


📩 **info@duilio-project.it** · 🌐 **https://duilio.cc**

You already have motors and drivers.  
What’s missing is **reliable and coordinated motion control behavior**.

Duilio F4 interfaces with control sources (RC receivers, PCs, Raspberry Pi or SBCs) and **any external motor driver**, embedding motion logic that usually gets reinvented every time: ramps, limits, coordination and failsafe.

## Intended use

Duilio F4 is a **development board** intended for **makers, advanced hobbyists and developers**,  
designed for **prototyping, experimentation and motion-control architecture development**.

It is **not currently certified as an industrial controller** and **not intended for safety-critical or life-critical applications**.

---

## What can you build with Duilio F4?

- **RC vehicles and machines**  
  Cars, boats, tracked vehicles, robotic platforms, remote lawn mowers.

- **Robots and mechatronic systems**  
  Differential drive, skid-steer, articulated mechanisms, linear actuators.

- **Custom servo motors of any power**  
  Turn **any motor + any driver** into a servo-like axis with limits, ramps and safety.

- **Rugged motion systems inspired by industrial practices**
  Consistent motion behavior using inexpensive or industrial drivers.


## Motors and drivers

Duilio F4 is **motor-agnostic** and **driver-agnostic**.  
If a driver can be controlled via **PWM, DIR, analog or RC-style signals**, Duilio F4 can manage it.

## Why Duilio F4?

Driving a motor is easy.  
Making a machine **behave predictably and safely** is not.

Duilio F4 removes the need to reinvent motion control logic, turning simple motor drivers into **motion-controller–like systems** — without writing custom application firmware.

**If you already have a motor driver, Duilio F4 makes it real motion control.**


---
## Key features — detailed overview

| Category | Feature | Details |
|--------|--------|--------|
| **MCU** | Microcontroller | STM32F411 (64-pin, Cortex-M4F) |
| | Real-time control | Deterministic real-time motion control handled on-board |
| | Firmware | Pre-developed, profile-based (no application code required) |
| |
| **Motion control** | Motor axes | **2 independent motion axes per board** |
| | Control modes | **Speed, position and torque control** |
| | Torque control | Via **external current sensors** |
| | Motion features | Acceleration / deceleration ramps, limits, soft limits |
| | Coordination | Axis coordination and motion mixing (profile-dependent) |
| | Safety | Interlocks, watchdogs and failsafe behaviors |
| |
| **Scalability** | Multi-board support | Native **RS485 multi-drop bus** |
| | System size | Designed for **10+ Duilio F4 boards** on the same bus |
| | Example | **10 boards = 20 motors**, centrally coordinated |
| | Architecture | One host, many Duilio nodes (distributed real-time control) |
| |
| **Motor drivers** | Driver type | External motor drivers only (no power stages on-board) |
| | Supported interfaces | PWM/DIR |
| | | ENABLE + DIR + PWM + STOP|
| | | Dual-PWM (forward / reverse) |
| | | STEP / DIR (speed or position usage) |
| | | Analog speed (0–5 V) |
| | | Analog speed + direction |
| | | RC-style PWM (ESC / servo pulse) |
| |
| **Encoders** | Absolute encoders | **2 I²C absolute encoders** |
| | Incremental encoders | **2 quadrature encoders (A/B)** |
| | Index / homing | **Z channel and limit switches supported** |
| | Usage | Position feedback, homing, zero reference |
| |
| **RC I/O** | RC inputs | **4 RC servo inputs** (PWM pulse capture) |
| | RC outputs | **4 RC servo outputs** |
| | Usage | RC receivers, ESCs, servos, mixed/manual control |
| |
| **Digital I/O (power)** | Power outputs | **4 NPN low-side outputs** |
| | Load type | External relays, solenoids, lamps |
| | Current | **< 2 A per channel** |
| | Control | Firmware-controlled, profile-dependent |
| |
| **Digital I/O (logic)** | Limit switches | End-stops and safety inputs |
| | Homing | Dedicated inputs for zeroing procedures |
| |
| **Analog input** | Analog channels | **2 analog inputs (0–5 V)** |
| | Usage | Torque reference, position reference (potentiometer), analog command |
| |
| **Sensors** | Ultrasonic sonar | **2 ultrasonic sonar interfaces (TRIG / ECHO)** |
| | Other sensors | Digital and analog sensors (profile-dependent) |
| |
| **Safety & failsafe** | Communication loss | Safe state on communication timeout |
| | | Configurable behavior on host or bus loss |
| | Startup safety | Motion enabled only after valid startup sequence |
| | | Optional gesture-based or multi-condition enable |
| | Interlocks | Hardware and firmware safety interlocks |
| | Emergency handling | Immediate output disable on fault conditions |
| | Watchdog | Internal watchdog and supervision logic |
| | Default state | Outputs forced to safe state at power-up |
| |
| **Configuration** | Programming interface | **ST-Link (SWD)** |
| | Configuration method | Firmware flashing and configuration via ST-Link |
| | USB | Optional / experimental, not the primary configuration interface |
| |
| **Host systems** | Supported hosts | Raspberry Pi, SBCs, PC, industrial computers |
| | Role separation | Host = logic / UI / networking |
| | | Duilio = real-time motion and I/O control |
| |
| **Power input** | VIN | **6 V – 43 V** |
| | USB | 5 V from USB |
| | Raspberry Pi | 5 V from Pi header (HAT mode) |
| |
| **Raspberry Pi power** | Output | Up to **5.1 V / 5 A** |
| | Purpose | Direct Raspberry Pi power supply |
| |
| **Protection** | Electrical | TVS, ESD, reverse and back-feed protection |
| | Environment | Designed for noisy motor environments |
| |
| **Configuration** | Tooling | **Duilio Tools** (no-code configuration) |
| | Advanced use | Direct firmware access possible |
| |
| **System philosophy** | Architecture | Motor-agnostic and driver-agnostic |
| | Reuse | Same control logic across different machines |

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

Duilio F4 can operate as a **standalone motion controller** or as part of a **host-controlled system**.

It can be driven by:
- RC receivers
- Raspberry Pi and other SBCs (Orange Pi, Rock Pi, Jetson Nano, …)
- standard PCs or industrial computers

When a host is present, Duilio F4 handles **deterministic real-time motion control and I/O**, while the host focuses on high-level logic, UI, networking or supervision.


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

## Get involved / Early access

Duilio F4 is entering the final hardware validation phase.

You can get involved in two ways:

**1. Contribute to the project**  
If you are interested in:
- motion control profiles
- real-world testing
- documentation or tools
- technical collaboration

your feedback and experience are welcome.

**2. Early access to the hardware**  
A limited number of **pre-production Duilio F4 boards** will be available for:
- beta testing on real machines
- early adopters and system integrators
- feedback-driven refinement before the first production batch

For the launch phase, the **target cost for early access boards is in the €20–30 range**,  
depending on configuration (e.g. THT connectors mounted or not) and production volume.

If you are interested in contributing or receiving early hardware access:  
📩 **info@duilio-project.it**  
🌐 **https://duilio.cc**



---
© 2026 Fabio Giuliodori — Duilio Project




