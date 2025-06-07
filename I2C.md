# I2C Communication Test - Calixto Systems Pvt Ltd

## Overview

This project demonstrates how to communicate with the Infineon OPTIGA Trust E security chip using I2C from userspace in a Linux environment. The code configures a GPIO reset line and performs I2C read/write operations to interact with specific device registers.

## Features

- Configures a GPIO pin to reset the OPTIGA device.
- Opens I2C bus and connects to OPTIGA Trust E at address `0x30`.
- Sends an "OpenApplication" APDU command.
- Reads I2C and DATA register states to verify device response.

## File Summary

- `optiga_test.c` – Main source file to control and communicate with the OPTIGA Trust E.
- `sysfs_gpio.h` – GPIO helper functions used for pin configuration.

## I2C Register Map Used

- `0x80` – DATA Register
- `0x81` – DATA Register Length
- `0x82` – I2C State
- `0x84` – Max SCL Frequency
- `0x90` – App State 0

## Modifying Configuration

To change the I2C bus or device address:

Update the following defines in optiga_test.c:

`#define OPTIGA_I2C_BUS 1`
`#define OPTIGA_ADDRESS 0x30`

To change the reset GPIO pin:

Update this section:

`GPIOExport(89);`
`GPIODirection(89, OUT);`
`GPIOWrite(89, HIGH);`

Replace 89 with the required GPIO number.

## Build Instructions

To compile the program:

`gcc optiga_test.c -o optiga_test`

Make sure `sysfs_gpio.h` and its implementation are in the same directory or properly linked.

## Run Instructions

Run the binary with root privileges:
```
sudo ./optiga_test
```
Expected output will show:

- Initialization and reset status
- I2C state before and after APDU command
- Response from the DATA register

## Dependencies

- Linux I2C and GPIO sysfs interfaces enabled.
- Standard C libraries and `linux/i2c-dev.h` must be available.
- Root access to access `/dev/i2c-*` and `/sys/class/gpio`

## License

© 2025 Calixto Systems Pvt Ltd. All rights reserved.
