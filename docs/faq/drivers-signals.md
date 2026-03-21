# Drivers & Signals

## Is Duilio tied to a specific driver?
No. The default logic matches ZS-X11-style drivers but is compatible with many common PWM/DIR drivers.

## Is Duilio compatible with 0–10 V drivers?
No. Duilio uses 5 V logic signals. External signal conversion is required.

## What is the minimum wiring per motor?
PWM and DIR are sufficient to move a motor.

## Do the solder jumpers on the analog/PWM outputs need to be closed?
No, not necessarily.

They are intended to improve analog signal stability, but in all performed tests no significant differences were observed.

For 20 kHz PWM operation, these solder jumpers must remain open.

## Why is the ENABLE pin recommended?
ENABLE allows Duilio to fully disable motion during faults or failsafe conditions, increasing safety.

## Can Duilio control stepper drivers?
Yes, if they support analog or 0–5 V control. STEP/DIR has not been fully tested yet.

## Is ZS-X11 required?
No. The default ENABLE and BRAKE logic is compatible with ZS-X11 and many common drivers that use PWM/DIR plus an enable line.

## Can I use a closed-loop driver?
Yes, for example a BLD300. For 4WD we recommend open-loop on the front axle, while Duilio handles the limiter and torque split logic.

## Can I use closed-loop motor drivers?
Yes. Closed-loop drivers such as BLD300 can be used.

## Should I use closed-loop drivers on all wheels?
In 4WD systems, open-loop control is recommended on the front axle, while Duilio manages speed limiting and torque distribution.
