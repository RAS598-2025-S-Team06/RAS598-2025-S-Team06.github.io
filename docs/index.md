---
title: Home
---

# Collaborative Robot Assistant for Object Transport & Assembly

## **Team Information**
**Team Members:** Jeremy Chen, Chieh Kao, Hsing-Cheng Wang<br>
**University and Semester:** Arizona State University, RAS598 Spring 2025<br>
**Professor:** Daniel Aukes


### **Introduction**
This project explores the development of a **Collaborative Robot**, which integrating a **TurtleBot 4 Lite** and a **UR5 robotic arm** for object transport and manipulation.  

**Research Question:**  
*"How can a mobile robot and a robotic arm effectively collaborate in an automated environment to transport and manipulate objects with minimal human intervention?"*  

This work is inspired by real-world warehouse automation and industrial robotics, where mobile robots transport items, and robotic arms handle detailed tasks like pick & place, sorting and assembly. The project will leverage **ROS 2 for communication, SLAM for navigation (TurtleBot).**  

---

### **Sensor Integration**
#### **How will sensor data be used in the code?**
- **TurtleBot 4 Sensors:**
  - **LIDAR & Depth Camera:** Used for SLAM-based navigation, object detection, and obstacle avoidance.
  - **IMU (Inertial Measurement Unit):** Helps improve localization and detect unexpected collisions.

- **UR5 Sensors:**
  - **Force-Torque Sensor (if available):** Provides haptic feedback for grasping adjustments.

---

### **Interaction & User Interface**
To control and monitor the robots, we need:  
- **Web Dashboard (ROS-based UI):** Displays robot status, object location, and execution progress.   
- **Physical Buttons (Emergency Stop & Manual Override):** Provides safety mechanisms.  

---

### **Control & Autonomy**
- **TurtleBot Autonomy:**
  - Uses **SLAM (Nav2)** for autonomous navigation.
  - Detects when it has reached the destination then sends a ROS signal, It can be a QR code on the wall.

- **UR5 Autonomy:**
  - Received the ROS signal, then go to pick and manipulate objects.
  - Put the objects to processing-ready zone, then pick the processed part to TurtleBot.
  - Sends a completion signal to the TurtleBot to continue to the next task.

**Feedback Mechanism:**  
- Sensors (camera, LIDAR, force-torque) provide real-time data.
- ROS 2 topics and services handle multi-robot communication.

---

### **Preparation Needs**
#### **Knowledge Requirements**
- **ROS 2 communication (Topics, Services, Actions)**
- **SLAM optimization for indoor navigation**
- **Motion planning & inverse kinematics (UR5)**

#### **Class Topics Needed**
- **Reinforcement learning** for dynamic path planning.
- **Edge AI processing** for real-time vision-based decision-making.

---

### **Final Demonstration**
The system will autonomously **transport an object via the TurtleBot 4**, and the **UR5 will manipulate it (pick & place)** in a real-world scenario.

#### **Resources Needed**
- **TurtleBot 4 with a carrying tray**
- **UR5 robotic arm on a sturdy table**


#### **Classroom Setup**
- Open floor space for TurtleBot navigation.
- A fixed workspace for UR5 operations.

#### **Handling Variability**
- The system will adapt to environmental changes (e.g., obstacles, lighting variations) using **SLAM**.

#### **Testing & Evaluation**
- **Navigation Accuracy:** Measure deviation from planned vs. actual path.
- **Grasping Success Rate:** Percentage of successful picks by UR5.
- **Task Completion Time:** Efficiency of transport and manipulation.
- **Error Recovery:** System’s ability to handle failures dynamically.

---

### **Impact**
This project contributes to the study of **multi-robot collaboration**, enhancing skills in **ROS 2, motion planning, SLAM, and perception**. The work has practical applications in **smart warehouses, logistics, and industrial automation**.  

By developing this project, we aim to create a **reproducible framework** for future multi-robot systems and inspire further research in **collaborative robotics**.

---
