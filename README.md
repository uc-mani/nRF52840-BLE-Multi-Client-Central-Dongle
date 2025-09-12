# nRF52840 BLE Multi-Client Central Dongle  

## Overview  
This project implements a **custom BLE dongle** using the Nordic **nRF52840 dongle**.  
The dongle runs on **Zephyr RTOS** and acts as a **Bluetooth Central**, capable of maintaining **multiple simultaneous connections** with peripheral devices.  

Instead of relying on the host operating system’s Bluetooth stack, the dongle manages all BLE communication itself and streams data over **USB serial** to a host application.  
This improves performance in multi-device scenarios and ensures cross-platform compatibility (Windows, Linux, macOS).  

---

## Features  
-  **Multi-client BLE central role** (tested with multiple simultaneous connections).  
-  **Lightweight serial protocol** for host communication.  
-  **Real-time notification streaming** from peripherals.  
-  **Read/Write characteristic access** from host PC.  
-  **MTU negotiation up to 447 bytes** for high-throughput communication.  
-  **Python host scripts** for scanning, connecting, and data exchange.  

---

## Repository Contents  
- `firmware/` → Zephyr-based source code for the nRF52840 dongle.  
- `docs/` → Documentation including architecture notes, serial protocol format, and testing results.  
- `examples/` → Python scripts showing how to interact with the dongle.  

---

## Requirements  
- **Hardware:** [nRF52840 Dongle (PCA10059)](https://www.nordicsemi.com/Products/Development-hardware/nRF52840-Dongle)  
- **Toolchain:** [Zephyr SDK](https://docs.zephyrproject.org/latest/getting_started/index.html) or [nRF Connect SDK](https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/getting_started.html)  
- **Host:** Python 3.10+ for running example scripts  

---

## Example Usage  

### Scan for nearby peripherals
```bash
python examples/scan_example.py
```

## Connect and subscribe to notifications
```bash
python examples/connect_and_notify.py --device <uuid>
```

## Read/Write a characteristic
```bash
python examples/read_write_example.py --device <uuid> --char <uuid> --data "1234"
```

## High-Level Architecture

### nRF52840 Dongle (Firmware)
 - Runs in central role
 - Manages scanning, connections, and GATT operations
 - Exposes a serial interface for host communication

### Host PC (Python Examples)
 - Sends serial commands (scan, connect, startnotif, read, write, etc.)
 - Receives responses and streamed notifications
 - Extendable for data collection or visualization

## License
This repository is shared for educational and portfolio purposes.

