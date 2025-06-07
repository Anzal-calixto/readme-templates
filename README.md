# CALIXTO SOM Peripheral Example Codes

This repository contains example C programs demonstrating how to interface and control various hardware peripherals on CALIXTO's System-on-Modules (SOMs). These examples are intended to help developers get started quickly with embedded Linux development.

## 🧩 Contents

The repository is organized by peripheral:

- `gpio/` – General Purpose Input/Output
- `uart/` – Serial Communication (UART)
- `i2c/` – Inter-Integrated Circuit (I2C)
- `spi/` – Serial Peripheral Interface (SPI)
- `adc/` – Analog-to-Digital Converter
- `can/` – CAN Bus Interface 

Each folder contains:
- Source code (`.c`, `.h`)
- Readme

## 🛠️ Target Hardware

These examples are developed and tested on the following PHYTEC platforms:

- **CALIXTO SOM**
- Other compatible CALIXTO boards

> ⚠️ Please refer to the individual example folder for specific hardware or pin configurations.

## 🧪 Requirements

- Toolchain: Cross-compiler for target architecture (e.g., `arm-poky-linux-gnueabi-gcc`)
- Host OS: Ubuntu 16.04+ recommended


## 🔧 Building the Examples

To build a sample:

```bash
steps
