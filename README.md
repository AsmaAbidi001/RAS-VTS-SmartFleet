# ROS2 Autonomous Robot – Differential Drive System

This project presents the development of a differential drive robot using ROS2, integrating embedded control, LiDAR-based perception, and real-time teleoperation.

The system combines hardware and software components to enable movement control, environment sensing, and basic mapping capabilities.

---

## 🔧 System Architecture

The robot is built around three main layers:

### 1. High-Level Control (ROS2)
- ROS2 Humble framework running on a Linux-based system
- Handles motion commands, communication, and mapping
- Processes velocity commands (`/cmd_vel`) and transforms them into motor actions

### 2. Embedded Layer (Arduino)
- Arduino Uno used as a motor controller
- Receives serial commands from ROS2
- Controls motor driver and auxiliary components (LED, relay)

### 3. Perception System
- RPLIDAR sensor for environment scanning
- Integrated with ROS2 for real-time data acquisition
- Used for mapping via SLAM algorithms

---

## ⚙️ Hardware Components

- Microcontroller: Arduino Uno  
- Processing Unit: PC / Raspberry Pi (ROS2 environment)  
- Motors: 4 DC motors  
- Motor Driver: L298N dual H-bridge  
- Sensor: RPLIDAR  
- Additional: Relay module and status LED  

---

## 🔌 Communication Mechanism

- Serial communication between ROS2 and Arduino (115200 baud)
- Custom command protocol:
  - Motor control: `CMD Lx Rx` (left/right PWM values)
  - Relay control: ON/OFF commands

The Arduino interprets commands and adjusts motor speed and direction accordingly.

---

## 🧠 Software Implementation

### ROS2 Nodes

- **Velocity Bridge Node**
  - Subscribes to `/cmd_vel`
  - Converts linear/angular velocity into PWM signals
  - Sends commands to Arduino via serial interface

- **Odometry Estimation Node**
  - Computes approximate robot position based on velocity
  - Publishes `/odom` and TF transformations

- **Teleoperation Node**
  - Keyboard-based control (WASD interface)
  - Enables manual navigation

---

## 🗺️ Mapping and Localization

- Integrated with `slam_toolbox`
- Uses LiDAR data to generate a 2D map
- Supports real-time environment visualization

---

## 🚀 Features

- Differential drive control  
- Real-time teleoperation  
- Serial communication with embedded system  
- LiDAR-based environment perception  
- Basic SLAM mapping  

---

## 🧪 Learning Outcomes

This project provided hands-on experience in:

- ROS2 architecture and node communication  
- Embedded systems integration (Arduino + Linux)  
- Sensor interfacing and real-time data processing  
- Robot control systems (kinematics & motion control)  
- Multi-layer system design  

---

## 👥 Team Contribution

This project was developed as part of a team during TSYP 13.0 (RAS Challenge).

My contributions included:
- Participation in system integration and testing  
- Support in ROS2 implementation and node configuration  
- Technical documentation and system structuring  
- Collaboration on hardware-software interfacing  

---

## 📌 Future Improvements

- Implement real odometry using encoders  
- Add autonomous navigation (path planning)  
- Improve control using PID algorithms  
- Optimize communication latency  
