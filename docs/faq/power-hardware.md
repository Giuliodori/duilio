# Power & Hardware Configuration

## Why is the Raspberry Pi power solder jumper left open by default?
Because the Raspberry Pi 5 V path is optional and should be enabled only deliberately. Leaving the solder jumper open keeps the standard protected 5 V rail separate from the Raspberry Pi GPIO 5 V path and reduces back-power risk.

## When should the Raspberry Pi power solder jumper be closed?
Only when you intentionally want DUILIO F4 to feed the Raspberry Pi through the GPIO 5 V path, or you have reviewed the complete 5 V power direction for the system.

## Can I power DUILIO F4 from the Raspberry Pi?
Yes, but only through the Raspberry Pi related 5 V path when the solder jumper is closed and the full power tree has been reviewed.

## Is it recommended to power both boards from each other?
No. Use one intended 5 V source and one intended power direction at a time. If the jumper is closed and more than one 5 V source is active, conflicting sources and back-powering can occur.

## Are all 5 V points on the board equivalent?
No. The standard 5 V output pins are on a protected branch with current limiting, while the Raspberry Pi GPIO 5 V branch changes behavior when the solder jumper is closed.

## What current is available on the protected 5 V branch?
For the standard protected 5 V outputs, communicate about 1.2 A nominal total on that protected branch.

## What changes when the Raspberry Pi 5 V jumper is closed?
Closing the jumper bypasses the current limiter only for the Raspberry Pi GPIO 5 V branch. That bypassed path is intended specifically to power the Raspberry Pi, not to turn every 5 V pin into the same rail.

## How much current can the Raspberry Pi branch provide?
As practical guidance, the Raspberry Pi bypass path should be considered suitable for about 2 A continuous and up to about 5 A peak, assuming the upstream 5 V source and wiring are sized accordingly.

## Why does DUILIO F4 not force a default power direction?
Because different installations require different power topologies, and forcing one would reduce flexibility. The safe rule is still to choose a single intended power direction before closing the jumper.

## What are BAT pins for?
Optional 3 V backup battery to preserve position memory and avoid re-homing.
