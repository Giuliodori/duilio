# 11. Debug & Service

This chapter describes the public service features available for troubleshooting, commissioning, and recovery.

## 11.1 Status LEDs
DUILIO F4 includes status LEDs for basic visual feedback during power-up, normal operation, and troubleshooting.
The exact blink patterns are firmware-defined and may vary between profiles or software revisions.

At user level, LEDs should be treated as quick health indicators, not as the only diagnostic method.

## 11.2 SWD debug interface
An SWD interface is provided for technical service, recovery, and low-level programming.
It should be used only by qualified users with appropriate tools.

WARNING: SWD access is not intended for normal operation and can interfere with system behavior.

## 11.3 Test points
Selected test and service access points are available for measurement and diagnostics during controlled service work.
They should be used with proper probes and stable fixtures.

WARNING: Avoid shorting adjacent points or probing live circuitry without appropriate precautions.
