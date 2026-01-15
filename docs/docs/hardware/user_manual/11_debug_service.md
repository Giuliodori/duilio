# 11. Debug & Service
This chapter describes the hardware service features available for troubleshooting and recovery.

## 11.1 Status LEDs
DUILIO F4 includes status LEDs for basic visual indication.
These LEDs are used to signal power presence, activity, or general status depending on firmware behavior.
Exact blink patterns are firmware-defined and may vary between profiles.

## 11.2 SWD debug interface
An SWD debug interface is provided for development, recovery, and manufacturing test.
It allows low-level access for programming and diagnostics when used with appropriate tools.
WARNING: SWD access is not intended for normal system operation and can interfere with real-time behavior.

## 11.3 Test points
Test points are exposed for measurement and diagnostic access during service.
They are intended for use with proper probing tools in controlled conditions.
WARNING: Avoid shorting adjacent test points or probing during operation without appropriate fixtures.
