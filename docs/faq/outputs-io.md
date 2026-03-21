# RC Outputs & I/O

## Can I connect small RC servos directly?
Yes. Small RC servos can be connected directly.

## What is the maximum current on RC outputs?
The standard auxiliary 5 V branch used by the RC outputs is current-limited to about 1.2 A nominal total.

## Why is current limited?
To protect the board and connected devices from overloads and short circuits on the protected 5 V branch.

## Can I power RC servos from RC outputs?
Yes, within the protected 5 V branch limit and the overall 5 V power budget.

## Is the Raspberry Pi 5 V path the same as the RC output 5 V rail?
No. If the Raspberry Pi 5 V jumper is closed, only the Raspberry Pi GPIO 5 V branch bypasses the limiter. That path is intended for Raspberry Pi power sharing, not as a generic 2 A supply on all 5 V pins.

## Can I connect an ESC BEC to RC outputs?
Yes. Protection diodes are present to prevent reverse current and unsafe back-feeding.

## Why are protection diodes used?
They prevent damage when multiple power sources are present, such as ESC BECs or external regulators.

## Can multiple BECs be connected?
It is recommended to use a single regulated source whenever possible to avoid conflicts.

## What can I connect to NPN outputs?
Relays, buzzers, and small loads. LED lighting up to about 20 W is supported.

## Can I move the status LED outside the enclosure?
Yes. The board ships without the LED installed; you can solder an LED or use 2.54 mm headers.
