This section lists all external connectors of the DUILIO F4.
Pin numbering follows the board silkscreen.
Signal direction and electrical limits are reported in the "Notes" column.
The electrical limits indicated per pin are subject to total current constraints of the board power system.

> NOTE: Power distribution and current limits (system-level)
> - Individual pin current ratings are maximum limits, not guarantees.
> - The sum of all output currents depends on the active power source.
> - When powered from VIN: total available 5 V current approx. 3 A continuous, 5 A peak (shared).
> - When powered ONLY from USB or Raspberry Pi GPIO: total available 5 V current < 0.8 A.
> - Exceeding the total budget may cause voltage drop, reset, or thermal shutdown.

### Connector J1 - Main supply input

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 1 | GND_PWR | Power ground (logic / signal reference) | 0 V reference, connect to system ground |
| 2 | +VCC | Main supply input (+VIN) | Input, main power supply (VIN range 6-43V) |

### Connector J2 - RS485 interface

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 3 | A+ | RS485 differential line A | Differential bus signal, do not apply external voltage |
| 4 | GND | Signal ground | 0 V reference |
| 5 | B- | RS485 differential line B | Differential bus signal, do not apply external voltage |

### Connector J3 - SWD programming

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 6 | SWDIO | SWD programming data | Programming/debug signal, 3.3 V logic |
| 7 | SWCLK | SWD programming clock | Programming/debug signal, 3.3 V logic |
| 8 | GND | Signal ground | 0 V reference |

### Connector J4 - Low-side digital outputs (OUT1-OUT4)

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 9 | OUT1 | Low-side digital output 1 (NPN) | Output, open-collector NPN, 2 A continuous (5 A peak, non-continuous) |
| 10 | OUT2 | Low-side digital output 2 (NPN) | Output, open-collector NPN, 2 A continuous (5 A peak, non-continuous) |
| 11 | OUT3 | Low-side digital output 3 (NPN) | Output, open-collector NPN, 2 A continuous (5 A peak, non-continuous) |
| 12 | OUT4 | Low-side digital output 4 (NPN) | Output, open-collector NPN, 2 A continuous (5 A peak, non-continuous) |
| 13 | +VCC | Main supply input (+VIN) | Power rail, VIN linked (same as +VCC main input) |
| 14 | +VCC | Main supply input (+VIN) | Power rail, VIN linked (same as +VCC main input) |

### Connector J5 - 5 V and GND distribution

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 15 | GND | Signal ground | 0 V reference |
| 16 | GND | Signal ground | 0 V reference |
| 17 | GND | Signal ground | 0 V reference |
| 18 | GND | Signal ground | 0 V reference |
| 19 | GND | Signal ground | 0 V reference |
| 20 | GND | Signal ground | 0 V reference |
| 21 | +5V | 5 V regulated output | Output, regulated 5 V, 0,5A |
| 24 | +5V | 5 V regulated output | Output, regulated 5 V, 0,5A |
| 25 | +5V | 5 V regulated output | Output, regulated 5 V, 0,5A |
| 26 | +5V | 5 V regulated output | Output, regulated 5 V, 0,5A |
| 27 | +5V | 5 V regulated output | Output, regulated 5 V, 0,5A |
| 28 | +5V | 5 V regulated output | Output, regulated 5 V, 0,5A |

### Connector J6 - RC inputs and analog inputs

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 29 | CH1_IN | RC channel 1 input (PWM) | Input, 5 V PWM signal, RC compatible (1-2 ms) |
| 30 | CH2_IN | RC channel 2 input (PWM) | Input, 5 V PWM signal, RC compatible (1-2 ms) |
| 31 | CH3_IN | RC channel 3 input (PWM) | Input, 5 V PWM signal, RC compatible (1-2 ms) |
| 32 | CH4_IN | RC channel 4 input (PWM) | Input, 5 V PWM signal, RC compatible (1-2 ms) |
| 33 | ADC1 | Analog input 1 (0-5 V) | Input, analog 0-5 V only, do not exceed 5 V |
| 34 | ADC2 | Analog input 2 (0-5 V) | Input, analog 0-5 V only, do not exceed 5 V |

### Connector J7 - I2C bus X

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 35 | GND | Signal ground | 0 V reference |
| 36 | +5V | 5 V regulated output | Output, regulated 5 V, total current shared 0,5A |
| 37 | SCL_X | I2C bus X - clock | Bidirectional, I2C clock, pulled-up to 5 V (5 V logic bus) |
| 38 | SDA_X | I2C bus X - data | Bidirectional, I2C data, pulled-up to 5 V (5 V logic bus) |

### Connector J8 - I2C bus Y

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 39 | GND | Signal ground | 0 V reference |
| 40 | +5V | 5 V regulated output | Output, regulated 5 V, total current shared 0,5A |
| 41 | SCL_Y | I2C bus Y - clock | Bidirectional, I2C clock, pulled-up to 5 V (5 V logic bus) |
| 42 | SDA_Y | I2C bus Y - data | Bidirectional, I2C data, pulled-up to 5 V (5 V logic bus) |

### Connector J9 - Motor driver interface (control signals)

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 43 | GND | Signal ground | 0 V reference |
| 44 | PWM_X | Motor X PWM output | Output, 5 V logic PWM signal to motor driver |
| 45 | ENA_X | Motor X enable output | Output, 5 V logic enable signal |
| 46 | RPM_X | Motor X speed feedback (RPM) | Input, digital speed feedback, max 5 V |
| 47 | BRK_X | Motor X brake output | Output, 5 V logic brake signal |
| 48 | DIR/PWM_X | Motor X direction or dual-PWM output | Output, 5 V logic, direction or dual-PWM mode |
| 49 | GND | Signal ground | 0 V reference |
| 50 | PWM_Y | Motor Y PWM output | Output, 5 V logic PWM signal to motor driver |
| 51 | ENA_Y | Motor Y enable output | Output, 5 V logic enable signal |
| 52 | RPM_Y | Motor Y speed feedback (RPM) | Input, digital speed feedback, max 5 V |
| 53 | BRK_Y | Motor Y brake output | Output, 5 V logic brake signal |
| 54 | DIR/PWM_Y | Motor Y direction or dual-PWM output | Output, 5 V logic, direction or dual-PWM mode |

### Connector J10 - User buttons

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 55 | B1 | User button input 1 | Input, active-low  5 V tolerant |
| 56 | B2 | User button input 2 | Input, active-low  5 V tolerant |
| 57 | B3 | User button input 3 | Input, active-low  5 V tolerant |
| 58 | GND | Signal ground | 0 V reference |

### Connector J11 - Raspberry Pi and ultrasonic sensors

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 59 | SCL_PI | I2C bus Raspberry Pi - clock | Bidirectional, I2C clock to Raspberry Pi header (3.3 V bus) |
| 60 | SDA_PI | I2C bus Raspberry Pi - data | Bidirectional, I2C data to Raspberry Pi header (3.3 V bus) |
| 61 | 5V | 5 V output (Raspberry Pi / peripherals) | Output, regulated 5 V 0,5A |
| 62 | GND | Signal ground | 0 V reference |
| 63 | TRG_Y | Ultrasonic sensor Y - trigger | Output, digital trigger, 5 V logic |
| 64 | ECO/ZY | Ultrasonic sensor Y - echo (or ZY input) | Input, echo signal, max 5 V |
| 65 | 5V | 5 V output | Output, regulated 5 V 0,5A |
| 66 | GND | Signal ground | 0 V reference |
| 67 | TRG_X | Ultrasonic sensor X - trigger | Output, digital trigger, 5 V logic |
| 68 | ECO/ZX | Ultrasonic sensor X - echo (or ZX input) | Input, echo signal, max 5 V |
| 69 | 5V | 5 V output | Output, regulated 5 V, total current shared 0.5 A |
| 70 | GND | Signal ground | 0 V reference |

### Connector J12 - RC PWM outputs

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 71 | CH4_OUT | RC output channel 4 (PWM) | Output, 5 V PWM signal, RC compatible |
| 72 | CH3_OUT | RC output channel 3 (PWM) | Output, 5 V PWM signal, RC compatible |
| 73 | CH2_OUT | RC output channel 2 (PWM) | Output, 5 V PWM signal, RC compatible |
| 74 | CH1_OUT | RC output channel 1 (PWM) | Output, 5 V PWM signal, RC compatible |
| 75 | 5V | 5 V output (RC / peripherals) | Output, regulated 5 V for RC / peripherals 2A PTC FUSE |
| 76 | GND | Signal ground | 0 V reference |

### Connector J13 - Backup battery

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 77 | BAT+ | Battery 3V for data save | External 3 V RTC backup battery only, do not connect to 5 V |
| 78 | GND | Signal ground | 0 V reference |

### Connector J14 - Raspberry Pi power and UART

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 79 | GND | Signal ground | 0 V reference |
| 80 | 5.1V | 5.1 V regulated output (Raspberry Pi supply) | Output, regulated 5.1 V, 3 A continuous (5 A peak), dedicated Raspberry Pi supply |
| 81 | TX-GPIO14 | UART TX (GPIO14) | Output, UART TX, 3.3 V logic |
| 82 | RX-GPIO15 | UART RX (GPIO15) | Input, UART RX, 3.3 V logic |
| 83 | GPIO17 | General purpose digital I/O | Bidirectional, GPIO, 3.3 V logic (not 5 V) |

### Connector J15 - USB data and power

| Pin number | Pin name (silkscreen) | Function | Notes |
| --- | --- | --- | --- |
| 84 | USB | USB data / power connection | USB data and power, USB data and power, onboard diode prevents external back-powering|
