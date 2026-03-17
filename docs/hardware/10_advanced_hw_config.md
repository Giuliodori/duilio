# 10. Advanced Hardware Configuration

This chapter describes non-default hardware configuration options intended for experienced integrators and service users.
Incorrect changes can cause malfunction, back-powering, or communication issues.

## 10.1 Power-related jumpers
Power-related solder jumpers configure non-default 5 V routing scenarios.
They must be changed only when the intended power direction is fully understood and documented for the machine.

Do not change jumpers while the board is powered.
WARNING: Incorrect jumper settings can create back-feeding paths and may damage the board, host, or connected peripherals.

## 10.2 Communication-related options
RS485-related hardware options may include termination and bias choices depending on the intended network.
These settings should only be changed when the bus topology is defined and verified.

For I2C integrations, verify only the necessary pull-ups are present and that cable routing is compatible with the expected signal integrity.

## 10.3 Service and recovery configuration
BOOT-related service access and SWD are provided for recovery, firmware service, and technical diagnostics.
These interfaces are not part of the normal end-user operating path and should remain in their default state during ordinary use.

WARNING: Misuse of service interfaces can prevent normal startup or interrupt system operation.
