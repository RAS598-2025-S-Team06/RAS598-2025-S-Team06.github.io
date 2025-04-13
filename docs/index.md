---
title: Home
---

# Collaborative Robot Assistant for Object Transport & Assembly

## **Team Information**
**Team Number:** 6 <br>
**Team Members:** Jeremy Chen, Chieh Kao, Hsing-Cheng Wang <br>
**Semester and Year:** Spring 2025 <br>
**School:** Arizona State University <br>
**Class:** RAS598 - Experimentation and Deployment of Robotic Systems <br>
**Professor:** Daniel Aukes <br>

### **Introduction**
As a variety of robots are being increasingly used in manufacturing settings, we are inspired to create a minimal project that covers the three aspects of automated manufacturing: application, collaboration, and simulation. In a real-world warehouse, mobile robots transport items, while robotic arms handle detailed tasks like picking & placing, sorting, and assembly. In this project we will leverage **ROS 2 for communication, SLAM for navigation (TurtleBot), and Gazebo for simulation.**  We will be integrating a **TurtleBot 4 Lite** and a **UR5 robotic arm** for object transport and manipulation. We would also like to dig into the concept of creating digital twins to simulate the behavior of each robot and further verify it with a real-world scenario.

**Research Question**  
*"A minimal automated manufacturing setting including an object transporting robot, object manipulating robot arm, and a real-time simulation."*  

**Sample Figure**
The following image is created by AI just for explanation purposes.
![alttext](./images/sample.jpg)

---

### **Sensor Integration**
#### **How will sensor data be used in the code?**
- **TurtleBot 4 Sensors:**
    - **LIDAR & Depth Camera:** Used for SLAM-based navigation, object detection, and obstacle avoidance.
    - **IMU (Inertial Measurement Unit):** Helps improve localization and detect unexpected collisions.
    - **Wheel rotation tracker:** For the localization of turtlebot.

- **UR5 Sensors:**
    - **Force-Torque Sensor:** Provides haptic feedback for grasping adjustments.

To utilize sensors on each robot, we are planning to feed the sensor input to our local host computer because we suspect the SLAM navigation will require a significant amount of computing power, which might be overwhelming for the Raspberry Pi on the turtlebot. By inputting the Lidar and Depth camera sensor data to local computing power, we will return the navigation result to the turtlebot to command its movement. As the turtlebot approaches the pickup destination, it will trigger a signal to start the UR5 robot arm. The robot arm will pick and place from the stack of objects and place it on top of the turtlebot. To correctly track the height of the stack of items, UR5 will utilize its torque sensor to gently tap the top of the stack to acquire the height of the topmost item. The UR5 will send this torque data to the local computer for height calculation as well as for simulation purposes. 

On the simulation end, UR5 will be sending out the angles of each actuator, which will then be used in the simulation to reflect the orientation of the robot arm. Similarly, the turtlebot will be sending the data from the wheel speed sensor and the IMU to host computer. The host computer will then integrate the data from the two sources, with the wheel speed sensor as the main input and the IMU as a reference in case of any unexpected incidents.


---

### **Interaction & User Interface**
To control and monitor the robots, we will be building a dashboard on the ROS-based UI. The dashboard will include to separate sections as shown in the figure below. On the left side will be the simulation, and on the right side will be all the controls needed. The controls will simply be start, stop, and emergency stop. Another window will show the path that is rendered from the data from Turtlebot.   

![alt text](./images/window_sample.png)


---

### **Control & Autonomy**
On TurtleBot, we will use SLAM for autonomous navigation, which will detect when it has reached the destination then sends a ROS signal, It can be a QR code on the wall for instance. On UR5, after receiving ROS signal from TurtleBot, robot arm will go to pick the parts from it and place it on the processing-ready zone. Then pick the processed part, place it on the TurtleBot. Finally, sends a completion signal to TurtleBot to continue the next task. 

---

### **Preparation Needs**
In order to build a Collaborative Robot Assistant with the TurtleBot 4 and UR5, we need to understand ROS 2 communication, including Topics for real-time data exchange, Services for request-response interactions, and Actions for handling asynchronous tasks. SLAM optimization is important for the TurtleBot’s accurate navigation, ensuring robust mapping and localization. For object manipulation, the UR5 relies on motion planning and inverse kinematics to do smooth and precise movements. Additionally, we will use Gazebo simulation for testing and refining the system in a virtual environment.

---

### **Final Demonstration**
In this demonstration, we will showcase a minimal automated manufacturing setup where a TurtleBot 4 autonomously navigates while transporting an object, and a UR5 robotic arm performs pick-and-place operations. The system will demonstrate real-time multi-robot collaboration, SLAM-based navigation, and adaptive object manipulation, simulating an industrial setting.

#### **Resources Needed**
- TurtleBot 4 with a carrying tray(maybe)
- UR5 robotic arm on a sturdy table
- TurtleBot 4 (possibly equipped with a carrying tray for object transport)
- UR5 robotic arm mounted on a sturdy table
- ROS 2-based computing setup for communication and coordination
- LiDAR, depth camera, IMU, and force-torque sensors for navigation and manipulation feedback
- Gazebo simulation environment for real-time digital twin verification
- Modular tables to construct an elevated track for TurtleBot 4, ensuring that the robot and UR5 arm operate at the same height.

#### **Classroom Setup**
- Open floor space: Ensuring sufficient area for TurtleBot 4 to navigate safely.
- Dedicated workspace for UR5: A fixed, stable table where the robotic arm will operate.
- Elevated Track System: Depending on demonstration needs, we may arrange tables to form a track-like platform for TurtleBot 4, allowing it to operate at the same height as the UR5 robotic arm. This will ensure seamless object transfer between the mobile robot and the robotic arm.
- Minimal environmental interference: Avoid excessive lighting changes or obstructions that may interfere with LiDAR and depth camera data.

#### **Handling Variability**
The system is designed to dynamically adapt to environmental changes by incorporating various strategies. TurtleBot 4 utilizes LiDAR and a depth camera to identify and avoid unexpected obstacles in real-time, ensuring smooth navigation. Depth sensors compensate for lighting variations, allowing the system to function reliably under changing light conditions. To handle uncertainty in object heights, the UR5’s force-torque sensor taps the top of stacked objects to determine their height, enabling precise grasping. Additionally, sensor-based feedback mechanisms ensure that if a grasp fails, the system will automatically reattempt pick-and-place operations with adjusted parameters. If necessary, the table track system allows the TurtleBot to maintain the required height alignment with the UR5, ensuring seamless interaction between the two components.

#### **Testing & Evaluation**
To validate the system’s performance, we will evaluate key metrics that reflect its accuracy, efficiency, and adaptability. Navigation accuracy will be assessed by comparing TurtleBot 4’s planned path with its actual trajectory, measuring deviations, and making necessary SLAM adjustments. The grasping success rate will be determined by calculating the percentage of successful object pickups by the UR5 robotic arm while optimizing grip strength and positioning based on failure rates. Task completion time will be measured to evaluate the overall efficiency of transport and manipulation, ensuring that each task is completed as swiftly as possible. Additionally, error recovery will be analyzed by examining the system’s ability to dynamically handle failures through mechanisms such as obstacle avoidance, reattempted grasps, and recalculated navigation paths.

---

### **Impact**
As ROS2 is a new topic for all of us, we can learn the valuable lesson of how to integrate different systems and also to create a simulation with Gazebo. By going through a hands-on deployment of our system, we can have a grasp on the basic topics including but not limited to:
1. The communication among multiple robots.
2. Creating a simulation with Gazebo.
3. Sensor fusion.

We aim to create a **reproducible framework** for future multi-robot systems.

---

### **Advising**
In the near future, we will need guidance from Prof. Aukes’s especially on SLAM and Gazebo for a collaborative robotic system. To fulfill multi-robot coordination, digital twin simulation, and real-world implementation, we will need Prof. Aukes’s advice on the data flow and possible barriers so we can ensure our project’s completion and all the interaction between the TurtleBot 4 Lite and UR5 robotic arm.

---
### **Gantt Chart Project Planning**
![alttext](./images/Gantt%20chart.png)

