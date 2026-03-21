# Power & Hardware Configuration

## Why is the Raspberry Pi power solder jumper left open by default?
Because powering the Raspberry Pi is optional and depends on the system architecture. Leaving the solder jumper open avoids accidental back-powering and unsafe power paths.

## When should the Raspberry Pi power solder jumper be closed?
It should be closed only if you want Duilio to power the Raspberry Pi from its supply rail.

## Can I power Duilio from the Raspberry Pi?
Yes. Closing the solder jumper allows the Raspberry Pi to power Duilio.

## Is it recommended to power both boards from each other?
No. It is strongly recommended to avoid powering both boards simultaneously from each other. Choose a single power direction to prevent conflicts and unintended current paths.

## Why does Duilio not force a default power direction?
Because different installations require different power topologies, and forcing one would limit flexibility and safety.

## What are BAT pins for?
Optional 3 V backup battery to preserve position memory and avoid re-homing.
