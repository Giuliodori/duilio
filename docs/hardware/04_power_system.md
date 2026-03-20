# 4. Power System

## 4.1 Power system overview

DUILIO F4 is a control board.  
It manages logic, field I/O, communication interfaces, and driver command lines, but it does not include motor power stages.

Three practical rules define the intended power architecture:

1. Motor power is always external.
2. DUILIO F4 distributes logic and auxiliary power only.
3. Only one intended 5 V power direction should be active in the final system.

**WARNING:** Do not route motor current through DUILIO F4.

---

## 4.2 Main input supply

The main board supply is **VIN**.  
The intended operating range is **7 V to 43 V DC**.

An **absolute maximum** condition is around **51 V transient class** (protection/survivability domain), and must **not** be treated as a continuous operating voltage.

VIN is used to feed onboard regulation and board-side low-power distribution.  
It is not a motor supply and must not be treated as a traction or actuator current path.

For field installations, VIN should come from a regulated or well-controlled DC source sized for the board and intended auxiliary loads.

The board includes filtering and protection elements intended to improve robustness during real installation use, including input-side transient suppression and filtered distribution on exposed interfaces.  
These features improve resilience to wiring noise and supply disturbances, but they do not replace correct system-level design.

---

## 4.3 Board power domains

DUILIO F4 exposes distinct practical power domains:

- logic and communication power for board electronics
- protected logic-side 5 V distribution
- RC / servo style auxiliary rail
- optional Raspberry Pi related 5 V path (hardware jumper dependent)

These domains are related, but they are not equivalent to a general-purpose power backplane for an entire machine.

---

## 4.4 System-level 5 V current budget

The board includes shared 5 V resources, so current must be evaluated at system level rather than pin-by-pin only.

Host-side Raspberry Pi 5 V sharing (JP1 closed) must be evaluated separately from the protected logic-side 5 V rail budget.

> **NOTE: Power distribution and current limits (system-level)**
> - Individual pin current ratings are maximum limits, not guarantees.
> - The sum of all output currents depends on the active power path and jumper configuration.

### Protected logic-side 5 V rail (through TPS2553)

- The protected `5V` rail is generated from `5V_RAW` through a current-limited switch.
- Configured limit is approximately **1.2 A nominal** (ILIM resistor dependent).
- Fault behavior includes current limiting, thermal shutdown, and auto-retry.

### Upstream 5 V availability

- Buck path (`5VBuck`) can supply the system according to converter/thermal conditions.
- USB path (`5VUSB`) depends on external host/source capability.
- Muxing between upstream 5 V sources is handled on board; available current still depends on source quality and wiring.

### Important

Exceeding the effective budget may cause:

- voltage drop
- brownout/reset
- thermal shutdown or cycling

This budget includes all 5 V loads connected to the board, including sensors, RC peripherals, and host-side 5 V sharing (if enabled).

---

## 4.5 Practical power scenarios

DUILIO F4 supports the following practical power scenarios.  
Each scenario assumes a clearly defined 5 V source and power direction.

### VIN-powered system

This is the normal full-operation scenario.  
VIN powers onboard regulation and the board distributes logic and auxiliary rails to supported loads.

Use this scenario for:

- normal machine integration
- dual-axis driver systems
- installations with external sensors and RC peripherals
- Raspberry Pi systems where DUILIO is the intended upstream source (if configured)

### USB-only bench setup

USB-only power is intended for bench work, communication tests, and light service operations.  
It is not intended to supply substantial external 5 V loads.

Use this scenario for:

- first board checks
- diagnostics
- software configuration
- no-load validation

### Raspberry Pi powered logic setup

In some compact integrations, 5 V may be shared with a Raspberry Pi depending on hardware jumper configuration.  
This must be a deliberate design choice, not a convenience connection.

Use this scenario only when:

- power direction is explicitly defined
- jumper configuration is known
- total 5 V load is compatible with the selected source

**WARNING:** Avoid simultaneous active 5 V sources unless the architecture explicitly guarantees isolation.

---

## 4.6 USB and host-side back-power risk

Back-powering is a configuration-dependent risk.

A critical condition exists when:

- the Raspberry Pi 5 V path jumper is **CLOSED**
- VIN-powered buck path is active
- Raspberry Pi is also powered externally (USB-C or other 5 V source)

In this case, two independent 5 V sources can be forced onto a shared path, which may lead to:

- unstable startup
- circulating current between supplies
- resets under load
- possible damage to Raspberry Pi or power circuitry

Safe usage rules:

- With jumper **CLOSED**:
  - use one intended 5 V source direction only
  - validate full system power tree before connection
- With jumper **OPEN**:
  - board-to-host 5 V path remains isolated at that jumper point

Typical mistake:

- VIN connected
- Raspberry Pi powered via USB-C
- jumper accidentally closed

**WARNING:** Never enable conflicting 5 V sources with the host-side 5 V jumper closed.

---

## 4.7 Raspberry Pi power path

DUILIO F4 can integrate with Raspberry Pi through dedicated host-side connections.  
The 5 V relationship depends on jumper configuration.

This path is intentionally not forced by default.  
It must be enabled only after deciding which device is the source and which is the load.

When the solder link is closed, behavior depends strongly on external source capability, wiring, and global system protection.

For hardware specification, treat this path as:

- suitable for moderate continuous current if source/connector/wiring are correctly sized
- unsuitable for uncontrolled source sharing
- requiring explicit system-level protection review

Design conditions:

- path intentionally enabled
- upstream source adequate
- wiring/protection dimensioned for expected load
- no conflicting 5 V source active

**WARNING:** If Raspberry Pi 5 V path is enabled, review the complete power tree before connecting USB to either device.

---
### Raspberry Pi current capability (JP1 closed)

When the Raspberry Pi 5 V path is enabled (JP1 closed), the host-side 5 V branch is tied to the board buck-side 5 V path.

Design guidance for public documentation:

- **Typical continuous target:** up to ~2 A (system-dependent)
- **Short peak events:** may be significantly higher only if source, thermal conditions, connector path, and wiring are validated
- Do **not** treat converter headline rating as guaranteed host-side current in all conditions

Important:
- This host-side branch is a **system-level integration path**, not an always-guaranteed fixed-power output.
- Verify voltage drop and temperature rise in the final installation.
 
## 4.8 Auxiliary 5 V and RC / servo rail

The board provides two distinct 5 V domains with different purposes.

### Protected logic-side 5 V rail (RC IN side)

The 5 V on the RC input side belongs to the board logic-side protected 5 V domain.

Typical uses:

- RC receivers
- sensors
- low-power peripherals

This rail is current-limited by onboard protection and intended for board-powered devices.

### Isolated AUX / RC OUT rail (servo power bridge)

The 5 V on RC output (AUX) side is **electrically separate from board logic 5 V** (`5V_SERVO` domain).

It is **not generated by the board logic regulator** and is intended as an external distribution bridge for servo/BEC style supply.

> **NOTE:** Even when AUX/servo 5 V is isolated from logic 5 V, **GND is shared**.

Typical usage:

- connect external BEC/servo supply
- distribute power to RC servos
- keep servo current independent from board logic-side 5 V

Important:

- this rail requires an external suitable source in the system architecture
- this rail is not the same protected logic-side 5 V domain
- do not assume board logic-side current limiting applies to high-current servo distribution

### Usage guidelines

Use protected logic-side 5 V for:

- onboard electronics
- low-power devices

Use AUX / RC OUT rail for:

- servo power from dedicated external source
- high-current loads that must remain separated from board logic-side 5 V

Do **NOT**:

- assume AUX rail is equivalent to logic protected 5 V
- tie AUX 5 V to logic 5 V unless explicitly engineered
- power high-current servos from protected logic-side rail

**WARNING:** Validate servo supply, wiring, and protection at system level.

---

## 4.9 Main input protection

The VIN input uses transient suppression and upstream protection strategy.

### TVS protection

The board includes VIN-side TVS suppression to clamp transient events and supply spikes.  
This improves survivability against short overvoltage events but does not replace upstream protection design.

Additional filtering/distribution elements are used to improve behavior in noisy environments and logic-side load transients.

### Fuse recommendation

The board includes an onboard fuse element on VIN, but this is not a replacement for full system protection strategy.

For safe operation, adding an external fuse on VIN is strongly recommended.

Why external fuse is recommended:

- limits fault energy at system level
- protects wiring/connectors
- reduces stress on onboard components
- simplifies service after faults

Recommended implementation:

- one series fuse on VIN
- typical range: 2 A to 5 A (installation dependent)
- choose fuse type (fast/slow) based on wiring, load profile, and environment

**WARNING:** Onboard protection is not a substitute for correctly sized system-level external fuse protection.

---

## 4.10 5 V rail protection

All exposed logic-side 5 V pins are fed through onboard 5 V protection stage (except paths intentionally bypassed by hardware configuration).

The protection stage limits current to approximately **1.2 A nominal total** and includes thermal shutdown/auto-retry behavior.

Practical effects:

- overloads and shorts are actively limited
- fault current is controlled
- persistent faults may cause cyclic restart behavior
- voltage may sag near current limit

Important:

- this is a protection mechanism, not an infinite 5 V source
- total current budget is shared across logic-side 5 V outputs

### Scope of protection

Protected (logic-side):

- RC input-side 5 V
- onboard logic-side 5 V outputs
- logic-side 5 V pins tied to protected `5V` domain

Not covered by the same protected path:

- AUX / RC OUT servo rail (`5V_SERVO` domain)
- host-side paths intentionally configured by jumpers

### System-level note

When host-side bypass/share paths are enabled (e.g. jumper configuration), protection behavior changes and must be evaluated at system level.

**WARNING:** The protected logic-side 5 V rail is current-limited (~1.2 A nominal), not an unlimited power source.

---

## 4.11 Backup battery

An optional 3 V backup battery can be used for retention-related functions supported by the system.  
It is not a primary board supply and does not power the main 5 V rail.

Use only intended battery type and polarity.  
Do not inject arbitrary voltage into backup battery connection.

---

## 4.12 Grounding strategy

DUILIO F4 requires a common signal reference with every connected external driver, host, and sensor.

Without a valid shared ground, logic signals (PWM, DIR, RS485, UART, trigger/echo, etc.) may behave unpredictably.

Typical wiring mistakes:

- signal lines without ground
- mixed supplies without defined common reference
- relying only on chassis/shield continuity as return path

**WARNING:** Always establish correct ground reference before enabling control outputs.

---

## 4.13 Power-related hardware configuration

Some power paths are influenced by solder jumpers or non-default hardware options.  
These are intended for controlled integration work, not casual end-user modification.

Do not change power-related jumpers while board is powered.  
Incorrect settings may create unsafe current paths, bypass intended protection behavior, or back-power connected equipment.
