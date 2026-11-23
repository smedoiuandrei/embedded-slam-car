# Embedded LiDAR Car

A keyboard-controlled robot car that uses a LiDAR sensor to map the area around it and detect obstacles, built around an **Arduino Nano 33 BLE Sense Rev2**.

Group project for the *Embedded Software for IoT* course at the University of Trento (UniTrento).

<!-- TODO: add a photo or GIF of the car / the live map here -->
<!-- ![Demo](docs/demo.gif) -->

---

## Overview

The car is driven remotely from a computer keyboard. While it moves, the LiDAR continuously scans its surroundings and the data is used to build a map of the environment, showing where the obstacles are relative to the car.

### Features

- Remote control of the car from the keyboard
- LiDAR scanning of the surrounding area
- Obstacle detection and visualization on a map
- Embedded firmware running on the Arduino Nano 33 BLE Sense Rev2

---

## Hardware

| Component | Details |
|---|---|
| Microcontroller | Arduino Nano 33 BLE Sense Rev2 |
| Distance sensor | Slamtec RPLIDAR A1 (2D 360° lidar) |
| Motors / driver | 2 geared DC motors with quadrature encoders on the rear wheels, 2× BTS7960 drivers |
| Steering | LD-1501MG servo |
| IMU (optional) | Bosch BNO085 |
| Chassis | 1:10 Ackermann RC chassis, rear-wheel drive |
| Power | 3S LiPo 11.1 V, 6000 mAh; XL4015 step-down converters |

### Vehicle parameters

| Parameter | Value |
|---|---|
| Wheelbase | 173 mm |
| Track width | 174.5 mm |
| Wheel radius | 29.9 mm |
| Encoder resolution | 660 counts per wheel revolution |
| Minimum turning radius | about 0.31 m left, 0.43 m right |

### Wiring

<!-- TODO: add a wiring diagram or a pin table -->

| Peripheral | Pin |
|---|---|
| LiDAR | [pin] |
| Motor driver | [pins] |

---

## Architecture

```
 Keyboard ──► Host computer ──[BLE / Serial]──► Arduino Nano 33 BLE Sense Rev2 ──► Motors
                   ▲                                         │
                   └───────────── LiDAR data ◄───────────────┘
```

- **Firmware** (`firmware/`): reads the LiDAR, drives the motors, and communicates with the host.
- **Host software** (`host/`): sends the keyboard commands and receives the LiDAR data to build and display the map.

---

## Getting Started

### Prerequisites

- Arduino IDE or PlatformIO
- Board package: *Arduino Mbed OS Nano Boards*

### Flash the firmware

1. Clone the repository:
   ```bash
   git clone https://github.com/smedoiuandrei/<repo-name>.git
   cd <repo-name>
   ```
2. Open `firmware/` in the Arduino IDE (or PlatformIO).
3. Select **Arduino Nano 33 BLE** as the board and the right port.
4. Upload the sketch.

### Run the host software

```bash
cd host
[install and run commands]
```

---

## Repository Structure

```
.
├── firmware/    # Code running on the Arduino Nano 33 BLE Sense Rev2
├── host/        # Control and mapping software on the computer
├── docs/        # Diagrams, photos, report
└── README.md
```

---

## Team

- Andrei Marius Smedoiu ([@smedoiuandrei](https://github.com/smedoiuandrei))
- Pietro Gelmini ([@Gelminaio](https://github.com/Gelminaio))
- Martin Gilmozzi ([@Marbanz](https://github.com/Marbanz))
- Giordano Pancher ([@AegirBooba](https://github.com/AegirBooba))

University of Trento, *Embedded Software for IoT*, A.Y. 2026/2027.

## License

MIT
