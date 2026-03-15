# TwinCAT3_Beckhoff_PLC

A collection of **reusable TwinCAT 3 / Beckhoff PLC libraries** for industrial automation projects. The repository provides structured, modular IEC 61131-3 code covering communication buses, field devices, and sensors — ready to drop into any TwinCAT 3 solution.

---

## Overview

| Area | What's included |
|------|----------------|
| **Communication Buses** | EtherCAT, CANopen, Modbus TCP/RTU, PROFIBUS, PROFINET, EtherNet/IP, serial (RS-232 / RS-485) |
| **Devices** | Drives / servo controllers, I/O terminals, vision systems, barcode readers, RFID readers, robots |
| **Sensors** | Proximity, photoelectric, pressure, temperature, flow, level, encoder / resolver |
| **Reusable Libraries** | Timers, counters, alarms, state-machines, PID controllers, data-logging, recipe management |

---

## Repository Structure

```
TwinCAT3_Beckhoff_PLC/
├── Communication/          # Bus-specific function blocks and helpers
│   ├── EtherCAT/
│   ├── CANopen/
│   ├── ModbusTCP/
│   ├── ModbusRTU/
│   ├── PROFIBUS/
│   ├── PROFINET/
│   └── Serial/
├── Devices/                # Device-level abstractions (drives, I/O, vision, …)
│   ├── Drives/
│   ├── IO_Terminals/
│   └── Barcode_RFID/
├── Sensors/                # Sensor interface blocks
│   ├── Proximity/
│   ├── Temperature/
│   ├── Pressure/
│   ├── Flow/
│   └── Encoder/
├── Libraries/              # General-purpose reusable utilities
│   ├── Alarms/
│   ├── PID/
│   ├── StateMachine/
│   ├── DataLogging/
│   └── RecipeManagement/
└── Examples/               # Sample TwinCAT 3 projects showing library usage
```

---

## Requirements

- **Beckhoff TwinCAT 3** (version 3.1 Build 4024 or later recommended)
- TwinCAT 3 PLC (XAE / XAR)
- Appropriate Beckhoff hardware or a TwinCAT 3 simulation runtime

---

## Getting Started

1. **Clone** this repository:
   ```bash
   git clone https://github.com/SujinM/TwinCAT3_Beckhoff_PLC.git
   ```
2. Open **TwinCAT XAE** (Visual Studio shell) and add the desired library project to your solution.
3. Reference the library in your PLC project via *References → Add Library*.
4. Instantiate the function blocks you need and wire them to your I/O.

---

## Communication Buses

### EtherCAT
Real-time Ethernet fieldbus used as the primary communication backbone for Beckhoff hardware.  
Function blocks handle master configuration, distributed-clock synchronisation, and CoE (CANopen over EtherCAT) parameter access.

### CANopen
Compliant with CiA 301 / 402 profiles. Includes SDO/PDO helpers and device-profile wrappers for drives and I/O nodes.

### Modbus TCP / RTU
Client and server function blocks for Modbus TCP (port 502) and Modbus RTU over serial. Supports all standard function codes (01–06, 15, 16, 23).

### PROFIBUS / PROFINET
Integration wrappers for PROFIBUS DP master/slave communication and PROFINET IO controller/device roles.

### Serial (RS-232 / RS-485)
Framing, buffering, and protocol helpers for serial communication, including ASCII and binary protocols.

---

## Devices

- **Drives / Servo Controllers** — axis control wrappers based on PLCopen Motion Control (MC2) function blocks.
- **I/O Terminals** — helpers for Beckhoff EL/EP/KL terminals (digital I/O, analog I/O, encoder, PWM).
- **Vision Systems** — trigger, result-read, and OK/NOK evaluation blocks for common smart-camera interfaces.
- **Barcode / RFID Readers** — serial and TCP read/write blocks with configurable framing.

---

## Sensors

- **Proximity & Photoelectric** — debounce and edge-detection blocks.
- **Temperature** — PT100/PT1000 linearisation, thermocouple cold-junction compensation.
- **Pressure & Flow** — analogue scaling, zero/span calibration, totaliser.
- **Level** — ultrasonic / radar echo-processing, tank-volume calculation.
- **Encoder / Resolver** — position, velocity, and acceleration calculation with overflow handling.

---

## Reusable Libraries

| Library | Description |
|---------|-------------|
| **Alarms** | Configurable alarm objects with timestamps, acknowledgement, and severity levels |
| **PID** | Standard PID with anti-windup, bumpless transfer, and auto-tuning hooks |
| **StateMachine** | Generic state-machine framework with transition logging |
| **DataLogging** | Cyclic and event-driven data logging to CSV / TwinCAT Scope |
| **RecipeManagement** | Read/write recipe sets from/to persistent storage |

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request. Follow the existing naming conventions (UPPER_CASE for function blocks, `fb` prefix for instances) and include XML documentation comments for every public interface.

---

## License

This project is licensed under the **GPL-3.0 License** — see [LICENSE](LICENSE) for details.
