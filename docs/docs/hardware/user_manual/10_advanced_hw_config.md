# 10. Advanced Hardware Configuration
This chapter describes non-default hardware configuration options intended for experienced integrators. Incorrect changes can cause malfunction or damage.

## 10.1 Power-related jumpers
Power routing jumpers configure how 5 V is distributed between DUILIO F4 and external systems. These are discussed in Chapter 4 and are open by default to avoid unsafe power paths.

Modify these jumpers only when a single, well-defined power direction is required for the system. Do not change jumpers while powered or during normal operation.
WARNING: Incorrect power jumper settings can cause back-feeding or damage to the board or the host.

## 10.2 Communication-related options
RS485 configuration uses solder jumpers to control termination and line biasing. Default settings are suitable for small networks; larger networks may require adjustment to avoid bus loading.
WARNING: Changes should be made only when the network topology is fully defined.

I2C hardware options are limited to external bus wiring and pull-up placement. Ensure only the required pull-ups are present in the system.

Additional RS485/I2C hardware options are defined by the specific system topology and external wiring choices.

## 10.3 Service and recovery configuration
BOOT configuration and SWD access are provided for service, recovery, and manufacturing use. These interfaces are intended for maintenance and should remain in their default state during normal operation.

Use BOOT configuration only for recovery or factory programming. Use SWD access for debugging and production testing.
WARNING: Misuse of service interfaces can prevent normal startup or interrupt system operation.
