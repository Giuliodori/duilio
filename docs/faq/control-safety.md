# Control & Safety

## Is DUILIO F4 a motor driver?
No. DUILIO F4 is a motion controller that works with external motor drivers.

## Why should I use DUILIO F4 if I already control my driver via RS485 from a PC?
Most RS485 drivers lack a true failsafe. If communication is lost, they often keep running with the last command. DUILIO F4 adds an independent safety layer that actively disables motion on command loss.

## Can't I implement failsafe logic on the PC?
PC-side software cannot guarantee deterministic behavior in case of crashes, freezes, or OS issues. DUILIO F4 runs safety logic locally and independently.

## What happens if communication is lost?
DUILIO F4 detects the loss and forces a safe state, disabling motion.

## Which control source has priority?
RC inputs always override USB commands to allow manual takeover.

## Can it be controlled by Raspberry Pi / PC over USB?
Yes. Use the provided Python or Arduino libraries to send commands over USB.

## Do RC commands override USB?
Yes. RC input has priority and acts as a manual takeover.

## Should I use USB or UART with a Raspberry Pi 5?
USB is more robust and recommended. UART over GPIO is more convenient for embedded wiring.
