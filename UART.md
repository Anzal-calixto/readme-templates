# UART Serial Communication Example

This project demonstrates how to use UART on the Calixto EVM or similar Linux-based embedded boards.

---

##  Requirements

- Linux-based development board (e.g., Calixto EVM)
- GCC compiler
- Access to serial device node (e.g., `/dev/ttySC3`)

---

##  Build the Code

```bash
gcc uart_example.c -o uart_example
```

---

##  Run the Program

```bash
sudo ./uart_example
```

---

##  Modify for Your UART Port

To use a different UART port:

1. Open the source file:

```bash
nano uart_example.c
```

2. Locate and update the following line:

```c
#define MODEMDEVICE "/dev/ttySC3"
```

3. Change `"/dev/ttySC3"` to match your system's UART device node (e.g., `"/dev/ttyUSB0"` or `"/dev/ttyS1"`).

4. Save and rebuild:

```bash
gcc uart_example.c -o uart_example
```

---

## Expected Output

```text
UART EXAMPLE
--------------------------------------------------------
Sent 
--------------------------------------------------------
Sent 
...
```

---

## Permissions Note

If you encounter permission errors when accessing the serial port:

```bash
sudo usermod -a -G dialout $USER
```



---

## License

