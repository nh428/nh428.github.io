---
layout: post
title: 'Autonomous LiDAR Guide Bot'
---

This project was started as a part of my coursework for ECE 5725, Embedded Operating Systems. Although my course has ended, I have since continued work and improvements as I've found it truly enjoyable. Even more in depth information about this project can be found in my end-of-year writeup, [here](https://nh428.github.io/ECE_5725_FinalProject/#intro).

## Objective:
My mission was to deisgn a device to help the visually impaired navigate through spaces they interact with often where traditional guiding methods may not be feasible. For example, in a labs or office workspace where a person makes infrequent navigations, a discrete, user-activated solution may be more practical than the continuous presence of a guide dog.

## Solution: 
My solution was a two part system consisting of an autonomous robot that traverses and maps a space in memory, then sends that data to a discrete wearable sensor capable of tracking a person's position and alerting them if they are approaching an obstacle. My robot uses a Raspberry Pi and LiDAR module to execute SLAM, autonmously navigating and mapping a space. Custom pathfinding algorithms direct its movement until a complete map is created. This data is then condensed and transmitted over bluetooth to a Pi Zero on the wearable tracker module. An IMU connected to the Pi Zero tracks the person's position in real time by counting steps, and calculates if the person is approaching an obstacle or deviating from a set path. If so, a piezoelectric buzzer goes off to notify the wearer, which stops when they go back on the path. There are many moving parts of this project, which I will go into on this page shortly :)

## Improvements
Although my course finished, I have continued work on improving this project. Here is what I'm currently working on improving:
- Increasing the accuracy of my SLAM mapping using better calibrated N20 motors with encoders, which are processed in parallel on an dedicated motor controller ESP32 to decrease latency. The reduancy of position calcualtion with encoders and LiDAR, as well as faster sensor processing with parallel chips both reduce error in the robot's percieved position vs its real position. The aim of this improvement is to increase the time I can run the bot before drift accumulates significantly. Eventually, I hope to build to a robot that can almost indefinitely navigate alongside its user with accuracy. 
- Improving robot's pathfinding algorithm accuracy, by creating more custom, targeted algorithms. By exploiting different aspects of common environments a robot might see itself in, my pathfinding robot can start to act "smart". If the robot notices it seems to be traveling down a hall, it should behave differently than if it notices its in a large room that is maxing out its LiDAR range. Given multiple pathfinding algorithms running in parallel, I am writing a control unit module that can dynamically assess the accuracy of the algorithm's desired path vs the path of best discovery so far. This way, I can favor certain targeted algorithms as the robot 'learns' about its environment through exploration.
- I also want to prioritize usability and user friendliness. I'm CADing the entire chassis to even weight distribution (which I expect to increase accuracy and eliminate the need for customn motor scaling factors), reduce profile, and increase energy effiecency. I am also looking at improving the person mounted module, reducing the profile by switching the Pi Zero to the smaller ESP32 C3 and switching the loud piezoelectric buzzer to a discrete vibration signal by adjusting the driving frequency or swapping to an ERM motor.
Lots of changes I'm chipping away at!

## Technicals
### SLAM + LiDAR
For the SLAM and LiDAR module, I am using a SLAMTEC C1 LiDAR scanner paired with [Alex Karavaev's ros2_laser_scan_matcher](https://github.com/AlexKaravaev/ros2_laser_scan_matcher) laser odometry module, built for ROS2 us1ing CSM. I have had success with this module, however down the road I'm looking into optimizing it for my use case. The LiDAR module communicates with 
