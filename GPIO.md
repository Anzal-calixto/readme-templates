
# GPIO Input and Output Control Application using gpiod Library.

-----------------------------------------------------------------------------------------------------------------------------------------
## 📁 File Structure

```
GPIO-Application/
├── gpio.c         # Application code to continuously toggle GPIO pins.
├── sysfs_gpio.c   # Contains the definitions for GPIO functions.
├── sysfs_gpio.h   # Contains declarations for GPIO functions.
```

## Description

1. This C program `gpio.c` allows you to control a GPIO output pin. It initializes a specific GPIO line and then sets its value to HIGH (1) or LOW (0). This is useful for tasks such as:

- Turning an LED ON or OFF  
- Controlling relays or other digital devices

## Key Features:

Lets you configure and set the output state (high/low) of a chosen GPIO pin.  
Simple and effective for hardware control like LED blinking or toggling.

2. This program also includes the capability to read the state of a GPIO input pin using the gpiod library. It is ideal for checking whether a button is pressed, a sensor is triggered, or any digital input is active (logic HIGH or LOW).

## Key Features: 
Allows you to read the current value (0 or 1) of a specified GPIO pin.  
Useful for applications like reading buttons, switches, or sensors.

--------------------------------------------------------------------------------------------------------------------------------------------

## Dependencies

- gcc or any C compiler  


--------------------------------------------------------------------------------------------------------------------------------------------

## Usage

1. Make sure the and C development headers are installed.  
2. Run `sudo gpiodetect` to find the GPIO chip (e.g., `/dev/gpiochip0`).  
3. Run `sudo gpioinfo gpiochip0` to find the correct GPIO line number.  
4. Update the `GPIO` value in the code accordingly.  
5. Compile and run the program:




--------------------------------------------------------------------------------------------------------------------------------------------
## Function:GPIOInit(bank, gpio,dir)
--------------------------------------------------------------------------------------------------------------------------------------------
Description:  
    Initializes the GPIO line for Input and output.

Parameters:  
    bank (int): gpio bank which the pin belongs to.
    gpio (int): Gpio pin number
    dir (int): Set gpio direction

Returns:  
    int 0 : if success
    int -1: if failure

--------------------------------------------------------------------------------------------------------------------------------------------
## Function: GPIOread(bank, gpio)
--------------------------------------------------------------------------------------------------------------------------------------------
Description:  
    reads the current value (0 or 1) of a specified GPIO pin

Parameters:  
    bank (int): Gpio bank which the pin belongs to.  
    gpio (int): Gpio pin number
    
Returns:  
    int 0 : if success
    int -1: if failure

--------------------------------------------------------------------------------------------------------------------------------------------
## Function: GPIOWrite(bank, gpio, value)
--------------------------------------------------------------------------------------------------------------------------------------------
Description:  
    Sets the GPIO line value to either HIGH (1) or LOW (0)
Parameters:  
    bank (int): gpio bank which the pin belongs to.
    gpio (int): Gpio pin number
    value (int): Set gpio value

Returns:  
    int 0 : if success
    int -1: if failure

--------------------------------------------------------------------------------------------------------------------------------------------
## Main Execution Logic
--------------------------------------------------------------------------------------------------------------------------------------------
1. Initialize the GPIO using GPIOInit()
2. Start a loop to Read the gpio values using GPIORead() and Toggle the GPIO ON and OFF every second using GPIOWrite()  
3. Press Ctrl+C to stop the loop

--------------------------------------------------------------------------------------------------------------------------------------------
## Example Output:
--------------------------------------------------------------------------------------------------------------------------------------------
```
    GPIO2_24 value = 1
    GPIO2_25 value = 1
```
--------------------------------------------------------------------------------------------------------------------------------------------
## Notes:
--------------------------------------------------------------------------------------------------------------------------------------------
- This program requires root privileges to access GPIO lines.  
- Adapt GPIO_PINS based on your hardware and available GPIO pins.
