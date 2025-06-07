# ADC Read Example - Calixto Systems Pvt Ltd

## Overview

This project demonstrates how to read analog input values from an ADC channel using the Industrial I/O (IIO) subsystem in Linux. It continuously reads values from a specific ADC channel and prints them to the terminal.

## File Structure

- `adc_test.c`: Contains the main logic to read raw ADC values from the sysfs IIO interface.

## How It Works

- The code reads from `/sys/bus/iio/devices/iio:device0/in_voltageX_raw`, where X is the ADC channel number.
- In this example, ADC channel `5`is used.
- The `ADC_Read()` function opens the file corresponding to the specified channel, reads the raw analog value, and returns it.
- The main loop continuously reads and prints the ADC value every 1 second.

## Modifying for Other Channels

To use a different ADC channel:

1. Locate the line in main():

   `ADC_Read(5);`

2. Replace 5 with your desired ADC channel number. For example:

   `ADC_Read(1);`    // Reads from ADC channel 1

3. Make sure the corresponding file exists:

   `/sys/bus/iio/devices/iio:device0/in_voltage1_raw`

Note: The available channels depend on your hardware and device tree configuration.

## Build and Run

To compile the code:

`gcc adc_read.c -o adc_read`

To run the compiled binary:
```
sudo ./adc_read
```

Note: Root permissions may be required to access the IIO sysfs entries.

## License

© 2025 Calixto Systems Pvt Ltd. All rights reserved.
