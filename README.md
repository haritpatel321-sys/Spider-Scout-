# HEXAPOD — Six-Legged Robot

A six-legged robotic platform designed for stable locomotion across different terrains. The project combines multi-servo leg actuation, programmable walking gaits, wireless communication, real-time video streaming, power management, and obstacle-avoidance capabilities.

## Authors

- **Harit Patel**
- **Nisarg Patel**
- **Khushi Padia**

---

## Project Overview

The Hexapod is a six-legged robotic platform inspired by insect locomotion. Its six-leg structure provides a stable support configuration and is intended to operate across uneven, rocky, soft, and other challenging terrains.

The project features:

- **18 degrees of freedom (DOF)**
- **3 servo motors per leg**
- Programmable walking gaits
- Real-time video streaming
- Bluetooth-based communication
- ESP32-CAM based vision
- Battery management and regulated power distribution
- Obstacle-avoidance capability

---

## System Architecture

The **Arduino Mega** is used as the main microcontroller for controlling the six legs.

**6 legs × 3 servos = 18 servo actuators**

```text
                         ┌────────────────────┐
                         │    Arduino Mega     │
                         │     ATmega2560      │
                         └─────────┬──────────┘
                                   │
             ┌─────────────────────┼─────────────────────┐
             │                     │                     │
          LEG 1                  LEG 2                  LEG 3
        3 Servos               3 Servos               3 Servos
             │                     │                     │
          LEG 4                  LEG 5                  LEG 6
        3 Servos               3 Servos               3 Servos

       HC-05 Bluetooth  ───────► Arduino Mega
       ESP32-CAM  ─────────────► Wi-Fi Video Streaming
       Battery ──► BMS ──► Buck Converters ──► System Power
```

---

## Main Components

| Component | Quantity | Purpose |
|---|---:|---|
| MG996R Servo Motor | 18 | Leg actuation |
| Arduino Mega 2560 | 1 | Main controller |
| HC-05 Bluetooth Module | 1 | Wireless communication |
| ESP32-CAM | 1 | Camera and video streaming |
| 3S 100A BMS | 1 | Battery management and protection |
| Buck Converter | 4 | DC voltage regulation |
| Battery Cells | 12 | Main power source |
| 3D-Printed Body Parts | — | Mechanical structure |

---

## Arduino Mega 2560

- Microcontroller: **ATmega2560**
- Operating voltage: **5 V**
- Recommended input voltage: **7–12 V**
- Digital I/O pins: **54**
- PWM-capable pins: **15**
- Analog input pins: **16**
- Flash memory: **256 KB**
- Clock speed: **16 MHz**

---

## MG996R Servo Motors

The robot uses **18 MG996R servo motors**, with three servos assigned to each leg.

- Operating voltage: **4.8–6 V DC**
- Working angle: **0–180°**
- Stall torque: up to **11 kg·cm at 6 V**
- Metal gears
- Three-wire interface: Signal, VCC, GND

---

## HC-05 Bluetooth Module

- Bluetooth: **2.0 + EDR**
- Frequency: **2.4 GHz ISM band**
- Communication: **UART**
- Default baud rate: **9600 bps**
- Approximate range: **10 m**
- Master/Slave operating modes

---

## ESP32-CAM Vision System

- ESP32-S dual-core processor
- OV2640 **2 MP camera**
- Wi-Fi connectivity
- Real-time video transmission
- Resolution up to **1600 × 1200**
- Frame rate up to **25 fps**
- IEEE 802.11 b/g/n Wi-Fi
- Bluetooth 4.2 support

---

## Power Management

The project uses a **3S battery configuration**, a BMS, and buck converters for regulated power distribution.

The battery arrangement consists of four cells connected in parallel in each series group, with three such groups connected in series.

```text
4 Cells Parallel ── Series Group 1 ──┐
4 Cells Parallel ── Series Group 2 ──┼──► 3S Battery Pack ──► BMS
4 Cells Parallel ── Series Group 3 ──┘
                                      │
                              Buck Converters
                                      │
                               System Power
```

The BMS provides:

- Cell balancing
- Overcharge/discharge protection
- Short-circuit protection

---

## Motion Control

The Hexapod uses coordinated movement of its six legs for stable locomotion.

### Programmable Gaits

The six legs are coordinated so that some legs maintain support while other legs move.

### Inverse Kinematics

Inverse kinematics is used to calculate leg-joint positions for desired foot positions.

### Adaptive Gait Control

The project considers adaptive gait algorithms for adjusting leg movements according to movement and terrain conditions.

### Terrain-Aware Movement

The project considers:

- Surface irregularities
- Real-time leg-placement adjustment
- Center-of-gravity maintenance

---

## Leg Configuration

Each leg consists of three servo-controlled joints. The setup procedure includes calibrating the initial angle of each servo before defining the required movement.

```text
             Servo 3
                │
             Servo 2
                │
             Servo 1
                │
             Leg Base
```

---

## Communication and Vision

### HC-05

Provides Bluetooth communication through UART.

### ESP32-CAM

Provides camera-based monitoring and Wi-Fi video streaming.

---

## Challenges and Project Approaches

### 1. Locomotion and Gait Complexity

**Challenge:** Coordinating six independent legs is more complex than bipedal or quadrupedal robots.

**Approaches:**
- Adaptive gait algorithms
- Inverse kinematics
- Terrain-aware walking
- Center-of-gravity maintenance

### 2. Mechanical Stability

**Challenge:** Maintaining structural strength while keeping the robot lightweight.

**Approaches:**
- Robust joint connections
- High-precision servo motors
- Shock-absorbing mechanisms
- Gyroscopic sensors and accelerometers for balance control

### 3. Power Management

**Challenge:** Managing energy consumption across multiple servo actuators and control electronics.

**Approaches:**
- Efficient power-distribution architecture
- Battery-management system
- Voltage regulation
- Adaptive power-management concepts

### 4. Control-System Complexity

**Challenge:** Synchronizing six legs with coordinated movement.

**Approaches:**
- Hierarchical control
- Low-level leg control
- High-level gait and path planning
- Distributed control concepts

---

## Project Cost

The total project cost reported in the project presentation is:

### **₹17,290**

| Component | Cost (₹) |
|---|---:|
| Servo motors ×18 | 6,300 |
| Arduino Mega | 1,300 |
| 3S 100A BMS | 450 |
| Buck converters ×4 | 900 |
| ESP32-CAM | 550 |
| Bluetooth module | 250 |
| 3D-printed body parts | 5,600 |
| Battery cells ×12 | 1,080 |
| Battery holders & wires | 220 |
| Pan & tilt couplers | 530 |
| Battery indicator | 45 |
| JST-SM connectors | 20 |
| DC pin plugs | 45 |
| **Total** | **17,290** |

---

## Key Features

- Six-legged robotic platform
- 18-DOF servo-based actuation
- Arduino Mega based control
- Programmable walking gaits
- Bluetooth communication
- ESP32-CAM video streaming
- BMS-based battery management
- Regulated power distribution
- Inverse-kinematics based leg-positioning concept
- Obstacle-avoidance capability
- 3D-printed mechanical structure

---

## Repository Structure

```text
hexapod-robot/
├── README.md
├── docs/
│   └── Hexapod_Corrected_Harit_Nisarg.pptx
├── hardware/
│   ├── circuit-diagram/
│   └── block-diagram/
├── firmware/
│   └── README.md
├── media/
│   └── project-images/
└── LICENSE
```

---

## Future Improvements

The project presentation identifies the following possible improvements:

- Advanced terrain-aware gait algorithms
- Improved balance control using gyroscopes and accelerometers
- Lightweight structural materials
- Distributed computing for leg control
- FPGA or dedicated microcontrollers for leg control
- Low-level PID control for individual leg movement
- Higher-level path and gait planning
- Machine-learning-based adaptive control

---

## Authors

**Harit Patel**  
**Nisarg Patel**  
**Khushi Padia**

**Project: HEXAPOD — Six-Legged Robot**
