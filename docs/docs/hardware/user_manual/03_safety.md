# 3. Safety Precautions

## 3.1 Safety symbols
Table 3-1 - Safety symbols and meaning

| Symbol | Meaning |
| --- | --- |
| Warning | Indicates a hazardous situation that could cause serious injury or equipment damage. |
| Caution | Indicates a hazardous situation that could cause minor injury or damage. |
| Note | Highlights important information or constraints. |
| Electrical hazard | Indicates risk of electric shock, overheating, or damage due to power. |

## 3.2 Device scope and limitations
DUILIO F4 is a control board, not a power driver and not a safety-rated device. Motor power never flows through DUILIO F4; external drivers and the mechanical system must handle emergency stops and safety interlocks. Integration must assume that power stages and safety functions are implemented outside the board.

> NOTE: Power distribution and current limits (system-level)
> - Individual pin current ratings are maximum limits, not guarantees.
> - The sum of all output currents depends on the active power source.
> - When powered from VIN: total available 5 V current approx. 3 A continuous, 5 A peak (shared).
> - When powered ONLY from USB or Raspberry Pi GPIO: total available 5 V current < 0.8 A.
> - Exceeding the total budget may cause voltage drop, reset, or thermal shutdown.

## 3.3 Electrical vs functional safety
Electrical safety concerns correct voltage, current, and insulation to avoid damage or shock. Functional safety concerns predictable system behavior under faults, including stopping motion safely. DUILIO F4 addresses electrical interface constraints only; functional safety must be provided by external drivers and system-level design.

## 3.4 Back-powering risks
Applying power simultaneously through VIN, USB, and GPIO sources can create unintended back-power paths. This can energize interfaces in an uncontrolled manner and may damage the host USB port or connected single-board computers. Avoid simultaneous power paths unless the system includes explicit isolation and power sequencing. Back-powering from a Raspberry Pi through the GPIO interface can also energize the board when VIN is off.

## 3.5 Motor and motion hazards
Motor systems can start unexpectedly due to firmware bugs, signal noise, or configuration errors. Perform initial tests on a bench with the mechanical load removed or decoupled, and secure the system to prevent motion. Disconnect motors or actuators during firmware debugging or interface validation.

## 3.6 Commissioning safety checklist
- Verify the supply type, polarity, and intended VIN usage before connecting power.
- Inspect the board and wiring for shorts, loose strands, or foreign objects.
- Confirm external power stages or drivers are correctly wired before enabling outputs.
- Keep motors or mechanical loads disconnected during the first power-up.
- Ensure only one power source is active unless isolation is present.
- Confirm an accessible power cutoff or emergency stop is available.
- Secure the board with standoffs and provide cable strain relief.
- Use a current-limited supply for initial validation.
