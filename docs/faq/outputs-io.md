# RC Outputs & I/O

## Can I connect small RC servos directly?
Yes. Small RC servos can be connected directly.

## What is the maximum current on RC outputs?
The current is automatically limited to approximately 2 A.

## Why is current limited?
To protect the board and connected devices from overloads and short circuits.

## Can I power RC servos from RC outputs?
Yes, within the current limit and power budget.

## Can I connect an ESC BEC to RC outputs?
Yes. Protection diodes are present to prevent reverse current and unsafe back-feeding.

## Why are protection diodes used?
They prevent damage when multiple power sources are present, such as ESC BECs or external regulators.

## Can multiple BECs be connected?
It is recommended to use a single regulated source whenever possible to avoid conflicts.

## What can I connect to NPN outputs?
Relays, buzzers, and small loads. LED lighting up to about 20 W is supported.

## Can I move the status LED outside the enclosure?
Yes. The board ships without the LED installed; you can solder a LED or use 2.54 mm headers.
