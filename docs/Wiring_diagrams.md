
Examinator – Complete Wiring Diagrams

 Overview
This document contains all wiring diagrams for connecting the hardware components.


 1. Sound Triangulation Module (4-Microphone Array)

 Components:
- 4x MAX9814 Microphone Modules
- 1x ESP32 Development Board
- Jumper wires

Connections:

Each Microphone (MAX9814) to ESP32:**

| MAX9814 Pin | ESP32 Pin | Function |
|-------------|-----------|----------|
| VCC | 3.3V | Power |
| GND | GND | Ground |
| OUT | GPIO32/GPIO33/GPIO25/GPIO26 | Audio Output (one per mic) |

Microphone Pin Assignments:**
- Mic 1 → GPIO32 (Front Left)
- Mic 2 → GPIO33 (Front Right)
- Mic 3 → GPIO25 (Back Left)
- Mic 4 → GPIO26 (Back Right)

Wiring Diagram (Text):
          +-------------------+
          |   ESP32 Board     |
          |                   |
  Mic 1 --+-> GPIO32          |
  Mic 2 --+-> GPIO33          |
  Mic 3 --+-> GPIO25          |
  Mic 4 --+-> GPIO26          |
          |                   |
3.3V ----+-> VCC (All Mics)   |
GND  ----+-> GND (All Mics)   |
          +-------------------+




2. Paper Detection Module (Thermal + UV + IR)

 Components:
- 1x MLX90640 Thermal Camera
- 4x UV LED Modules (365nm)
- 4x IR Proximity Sensors (Sharp GP2Y0A21YK0F)
- 1x Arduino Nano

Connections:

MLX90640 Thermal Camera to Arduino Nano:**

| MLX90640 Pin | Arduino Nano Pin | Function |
|--------------|------------------|----------|
| VIN | 3.3V | Power |
| GND | GND | Ground |
| SCL | A5 | I2C Clock |
| SDA | A4 | I2C Data |

UV LED Modules to Arduino Nano:**

| UV LED Pin | Arduino Nano Pin | Function |
|------------|------------------|----------|
| VCC | 5V | Power |
| GND | GND | Ground |
| DIN | D3 | Digital Control |

IR Proximity Sensors to Arduino Nano:**

| IR Sensor Pin | Arduino Nano Pin | Function |
|---------------|------------------|----------|
| VCC | 5V | Power |
| GND | GND | Ground |
| VOUT | A0, A1, A2, A3 | Analog Output |

 Wiring Diagram (Text):
+-------------------+
|   Arduino Nano    |
|                   |


Thermal SCL ----+-> A5              |
Thermal SDA ----+-> A4              |

UV LED -------->+-> D3              |

IR 1 (VOUT) --->+-> A0              |
IR 2 (VOUT) --->+-> A1              |
IR 3 (VOUT) --->+-> A2              |
IR 4 (VOUT) --->+-> A3              |




3. Phone Detection Module

Components:
- 3x ESP32 Development Boards
- 1x RTL-SDR Dongle
- 1x Antenna Kit

Connections:

ESP32 Boards (each) to USB Hub:**

| ESP32 Pin | USB Hub Port | Function |
|-----------|--------------|----------|
| USB | Port 1-3 | Power + Serial |

RTL-SDR Dongle to USB Hub:**

| RTL-SDR | USB Hub Port | Function |
|---------|--------------|----------|
| USB | Port 4 | Power + Data |

Antenna Connection:**
- SMA Antenna → RTL-SDR SMA Connector

Wiring Diagram (Text):
          +-------------------+
          |   USB Hub         |
          |                   |
ESP32 #1 -+-> Port 1          |
ESP32 #2 -+-> Port 2          |
ESP32 #3 -+-> Port 3          |
RTL-SDR --+-> Port 4          |
          |                   |
          +-------------------+
                 |
           [Raspberry Pi]


           


4. Complete System Overview

 All Modules Connected:
 ┌─────────────────────────────────────────────────────────────┐
│                     POWER SUPPLY (5V 4A)                    │
│                                                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Raspberry  │  │  USB Hub     │  │  Speakers    │      │
│  │   Pi 5       │  │  (7-port)    │  │             │      │
│  └──────┬───────┘  └──────┬───────┘  └──────────────┘      │
│         │                 │                                 │
│    [USB]│           [USB] │                                 │
│         │                 │                                 │
│  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────────┐      │
│  │  WiFi Cameras│  │  ESP32s      │  │  Arduino     │      │
│  │  (x2)        │  │  (Phone)     │  │  Nano        │      │
│  └──────────────┘  └──────────────┘  └──────┬───────┘      │
│                                              │               │
│                                         ┌────┴────┐         │
│                                         │ Mics    │         │
│                                         │ (x4)    │         │
│                                         ├─────────┤         │
│                                         │ Thermal │         │
│                                         │ UV LEDs │         │
│                                         │ IR      │         │
│                                         └─────────┘         │
└─────────────────────────────────────────────────────────────┘






5. Power Distribution

Power Requirements:

| Component | Voltage | Current (Estimated) |
|-----------|---------|---------------------|
| Raspberry Pi 5 | 5V | 3A |
| WiFi Cameras (x2) | 5V | 0.5A each |
| USB Hub | 5V | 1A |
| ESP32 Boards (x4) | 3.3V | 0.2A each |
| Arduino Nano | 5V | 0.1A |
| RTL-SDR Dongle | 5V | 0.2A |
| Speakers | 5V | 0.5A |
| **Total** | - | **~5.5A** |

 Recommendation:
- Use a **5V 6A power supply** for reliable operation
- Use high-quality USB cables to avoid voltage drop

---

6. Pin Summary Table

 ESP32 (Sound Hub):

| Pin | Function | Connected To |
|-----|----------|--------------|
| 3.3V | Power | Mics VCC |
| GND | Ground | Mics GND |
| GPIO32 | Audio In | Mic 1 OUT |
| GPIO33 | Audio In | Mic 2 OUT |
| GPIO25 | Audio In | Mic 3 OUT |
| GPIO26 | Audio In | Mic 4 OUT |

ESP32 (Phone Detection) – Each Board:

| Pin | Function | Connected To |
|-----|----------|--------------|
| USB | Power + Data | USB Hub |

Arduino Nano:

| Pin | Function | Connected To |
|-----|----------|--------------|
| 3.3V | Power | Thermal VIN |
| 5V | Power | UV + IR VCC |
| GND | Ground | All GND |
| A4 | I2C Data | Thermal SDA |
| A5 | I2C Clock | Thermal SCL |
| D3 | Digital Out | UV LEDs DIN |
| A0 | Analog In | IR 1 |
| A1 | Analog In | IR 2 |
| A2 | Analog In | IR 3 |
| A3 | Analog In | IR 4 |

Raspberry Pi 5:

| Port | Connected To |
|------|--------------|
| USB | USB Hub |
| USB | WiFi Cameras |
| Audio Jack | Speakers |
| Ethernet | Network |
| HDMI | Display |
 
