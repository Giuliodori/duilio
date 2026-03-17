# 4. Power System

## 4.1 Power system overview

DUILIO F4 is a control board.
It manages logic, field I/O, communication interfaces, and driver command lines, but it does not include motor power stages.

Three practical rules define the intended power architecture:

1. Motor power is always external.
2. DUILIO F4 distributes logic and auxiliary power only.
3. Only one intended 5 V power direction should be active in the final system.

WARNING: Do not route motor current through DUILIO F4.

## 4.2 Main input supply

The main board supply is VIN.
The intended operating range is 7 V to 43 V DC, with 51 V as absolute maximum.

VIN is used to feed the onboard regulation and the board-side low-power distribution.
It is not a motor supply and must not be treated as a traction or actuator current path.

For field installations, VIN should come from a regulated or well-controlled DC source sized for the board and the intended auxiliary loads.

The board includes filtering and protection elements intended to improve robustness during real installation use.
These include input-side transient protection, filtered power distribution, and protection on exposed board interfaces.
They help reduce sensitivity to wiring noise and supply disturbances, but they do not replace correct system-level design.

## 4.3 Board power domains

DUILIO F4 exposes distinct practical power domains:

- logic and communication power for the board electronics
- auxiliary 5 V distribution for supported peripherals
- RC / servo style auxiliary rail
- optional Raspberry Pi related 5 V path depending on jumper configuration

These domains are related, but they are not equivalent to a general-purpose power backplane for an entire machine.

## 4.4 System-level 5 V current budget

The board includes shared 5 V resources, so current must be evaluated at system level rather than pin by pin only.

> NOTE: Power distribution and current limits (system-level)
> - Individual pin current ratings are maximum limits, not guarantees.
> - The sum of all output currents depends on the active power source.
> - When powered from VIN: total available 5 V current approx. 3 A continuous, 5 A peak (shared).
> - When powered ONLY from USB or Raspberry Pi GPIO: total available 5 V current is typically < 0.8 A and depends on the actual source capability.
> - Exceeding the total budget may cause voltage drop, reset, or thermal shutdown.

This budget includes all 5 V loads connected to the board, including sensors, RC peripherals, and any host-side 5 V sharing that the selected configuration allows.

## 4.5 Practical power scenarios

DUILIO F4 supports the following practical power scenarios.

### VIN-powered system

This is the normal full-operation scenario.
VIN powers the onboard regulation and the board distributes logic and auxiliary rails to supported loads.

Use this scenario for:

- normal machine integration
- dual-axis driver systems
- installations with external sensors and RC peripherals
- Raspberry Pi systems where DUILIO is the intended upstream source

### USB-only bench setup

USB-only power is intended for bench work, communication tests, and light service operations.
It is not intended to supply substantial external 5 V loads.

Use this scenario for:

- first board checks
- diagnostics
- software configuration
- no-load validation

### Raspberry Pi powered logic setup

In some compact integrations the 5 V path may be shared with a Raspberry Pi, depending on the selected hardware configuration.
This must be treated as a deliberate system design choice, not a casual convenience connection.

Use this scenario only when:

- the power direction is explicitly defined
- jumper configuration is known
- the total 5 V load remains compatible with the source

WARNING: Avoid simultaneous active 5 V sources.

## 4.6 USB and host-side back-power risk

Back-powering is one of the main integration risks on this board family.
It can occur when USB, Raspberry Pi 5 V, and externally generated 5 V are allowed to meet without a single intended power direction.

Potential consequences include:

- unstable startup
- phantom powering of logic sections
- resets under load
- damage to the USB host or Raspberry Pi

WARNING: One intended 5 V source, one intended power direction.

## 4.7 Raspberry Pi power path

DUILIO F4 can be integrated with a Raspberry Pi through the dedicated host-side connections.
The 5 V relationship between the two devices depends on the hardware jumper configuration.

The Raspberry Pi related 5 V path is intentionally not forced by default.
It must be treated as a controlled option that the integrator enables only after deciding which device is the source and which device is the load.

When the related solder link is closed, current limiting and fault behavior depend more strongly on the external source and the overall system design.

For the public hardware specification, the intended Raspberry Pi supply path should be considered suitable for less than 2 A continuous current, with short peak demand up to 5 A, provided that:

- the path is intentionally enabled
- the upstream source is adequate
- wiring and protection are dimensioned for the expected load
- no conflicting 5 V source is present in the system

WARNING: If the Raspberry Pi 5 V path is enabled, review the complete power tree before connecting USB to either device.

## 4.8 Auxiliary 5 V and RC / servo rail

The board exposes auxiliary 5 V outputs for supported peripherals, RC devices, and similar low-power accessories.
These rails are convenient integration points, but they are still part of the shared power budget.

Use the auxiliary rail for:

- RC receivers
- supported sensors
- low-power external logic
- small servo-style peripherals within the allowed budget

Do not use the auxiliary rail for:

- motor power
- large inductive loads
- heavy servo clusters without explicit current review
- external devices whose startup current exceeds the shared budget

WARNING: A protected 5 V rail is not the same as an unlimited external power output.

## 4.9 Main input protection

The main VIN input uses a transient protection approach based on onboard suppression plus external upstream protection.

### TVS protection

The board includes a TVS protection element on the VIN side to clamp transient events and supply spikes.
This improves survivability against short overvoltage events but does not replace correct upstream protection.

Additional filtering and distribution elements are present on the board to improve behavior in noisy electrical environments and during load transients on the logic side.

### External fuse requirement

An external fuse on VIN is part of the intended protection concept.
Without it, a sustained fault can force the protection network to absorb more energy than intended.

Recommended public guidance:

- one fuse in series with VIN
- typical range 2 A to 5 A depending on the installation
- choose the fuse type according to the application and wiring environment

## 4.10 5 V rail protection

The main 5 V distribution uses resettable PTC protection.
This helps limit overload current and reduces fault energy during shorts or wiring mistakes.

Important practical points:

- PTC devices limit fault current, they do not regulate power
- voltage drop can increase before full trip
- recovery is not instantaneous
- repeated overloads can still lead to unstable behavior during integration

When a Raspberry Pi related bypass path is intentionally enabled, the resulting protection behavior changes and must be reviewed at system level.

## 4.11 Backup battery

An optional 3 V backup battery can be used for retention-related functions supported by the system.
It is not a primary board supply and does not power the main 5 V rail.

Use only the intended battery type and polarity.
Do not inject arbitrary voltage into the backup connection.

## 4.12 Grounding strategy

DUILIO F4 requires a common signal reference with every connected external driver, host, and sensor.
Without a valid shared ground, logic signals such as PWM, DIR, RS485, UART, or trigger/echo lines can behave unpredictably.

Typical wiring mistakes include:

- connecting signal lines without ground
- mixing supplies without defining a common reference
- relying on chassis or shield continuity as the only signal return path

WARNING: Always establish a correct ground reference before enabling control outputs.

## 4.13 Power-related hardware configuration

Some power paths are influenced by solder jumpers or non-default hardware configuration choices.
These options are intended for controlled integration work, not for casual end-user modification.

Do not change power-related jumpers while the board is powered.
Incorrect settings can create unsafe current paths, bypass intended protection behavior, or back-power connected equipment.
