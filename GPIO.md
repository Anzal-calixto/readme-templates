# GPIO Test - Calixto Systems Pvt Ltd

## Overview

This project provides a simple test for GPIO control using the sysfs interface in Linux. It initializes specific GPIO pins as input and output and toggles the output pins while reading the input states.

## File Structure

- `gpio.c`: Main application file to initialize and test GPIO functionality.
- `sysfs_gpio.h`: Header file containing prototypes and macros.
- GPIO handling logic uses the sysfs interface (`/sys/class/gpio`) for configuration and value read/write.

## How It Works

- Inputs: `GPIO2_24` and `GPIO2_25`
- Outputs: `GPIO2_22` and `GPIO2_23`

In an infinite loop:
- Reads the values of input pins.
- Toggles the output pins every 1 second (LOW to HIGH and vice versa).

## Modifying for Other GPIOs

To use different GPIOs:

1. Identify your target GPIO bank and pin number.
2. Modify the following lines in `main()` of gpio.c:

   `GPIOInit(BANK, PIN, DIRECTION);`

   - Replace `BANK` with the GPIO bank number.
   - Replace `PIN` with the GPIO number within the bank.
   - Use `IN` for input and `OUT` for output.

   Example:

   `GPIOInit(1, 17, IN);`   // Initializes GPIO1_17 as input  
   `GPIOInit(3, 15, OUT);`   // Initializes GPIO3_15 as output

3. Update `GPIORead()` and `GPIOWrite()` calls accordingly to reflect the new pins.

## Build and Run

To compile:

`gcc gpio.c -o gpio_test`

To run:
```
sudo ./gpio_test
```

Note: Root privileges are required to access GPIO via sysfs.

## License

© 2025 Calixto Systems Pvt Ltd. All rights reserved.
