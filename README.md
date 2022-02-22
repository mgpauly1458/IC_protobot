# IC_protobot

## Overview

This is a clone of the shared project repository made by the members of the [University of Hawaii Robotic Space Exploration Team](https://manoa.hawaii.edu/uh-vip/project/robotic-space-exploration-rose-vip/). Our team's goal is to creat a six wheeled robot that can drive, operate a manipulator arm, detect life, and autonomously navigate which we will officially enter into the [University Rover Challenge](https://urc.marssociety.org/home), June 2022. This repository contains the software module prototypes which we worked diligently on in order to prove the architectural concepts laid out in our Critical Design Review(link).

Contributors: Maxwell Pauly, Bret Witt, Ashten Akemoto, Jacob Sequeira, Jeraldine Milla, Stephanie Alemore, and Zolbo Tomita.

Picture of the robot currently used for prototyping:
<br>
![image](https://user-images.githubusercontent.com/74911365/155123497-79ac5871-d912-4ee8-9e1f-668debe898f1.png)


## Robot Operating System (ROS)

ROS is an open source robotics middleware suite and is the premier framework for robotic rapid prototyping. The [ROS wiki](https://www.ros.org/) is an outstanding resource to learn more so I won't go into detail here. The project uses ROS for the majority of the robot's communication between components and functionality. Each software developer on the project completed the [ROS Tutorials](http://wiki.ros.org/ROS/Tutorials) and below is a demonstration of ROS nodes talking to one another and executing commands.


https://user-images.githubusercontent.com/74911365/154920396-d8579ff4-1784-4360-8b3e-b7f285558c4d.mp4



## Gazebo Simulation

## Web App Graphical User Interface (GUI)
<br>
A GUI is needed to contorl the robot and subsequently compete in the URC competition. The stack begins with a simple web app which interfaces with the ROS network via a web socket. Commands are transferred wirelessly (with generous bandwidth limitations) using 802.11 WiFi and the http protocol. The web server was made using Node.js and Express. The data is displayed to the operator using html/css/javascript. The video below shows a demo of the latest prototype where a video feed and three topics are displayed on the homepage. 

The latest GUI prototype can display video output, and topic data. The up and down arrows are pressed on the keyboard and which sends velocity commands to ROS, which can be seen at the bottom of the display.
<br>
https://user-images.githubusercontent.com/74911365/154946249-04c9510b-1193-423e-aa36-a8eb3eec0615.mp4


An earlier prototype, text input in an html form is sent to the ROS network and broadcasted by a node.
https://user-images.githubusercontent.com/74911365/140019513-80895195-2fa0-49e1-8030-edcdf03711ba.mp4


## Motor Encoders
The robot uses ten motors, six for forward and backward acceleration and four for steering. We are using the (https://www.pololu.com/product/3284) Roboclaw motor encoders which communicate over serial ports. A 'roboclaw' object was created using C++ which acts as the bridge between the linux serial ports and the actual encoders (source(link)). This object is used by the ROS node (source(link)) to properly send and recieve data and control when the wheels spin.

(video of ros sending and recieving data and turning the wheels)

## Arm Simulation

## Installation

### Dependencies

##### sudo apt update
##### sudo apt upgrade
##### sudo apt-get install ros-noetic-rosbridge-suite ros-noetic-rosbridge-server nodejs npm

### Getting Started:

#### Terminal 1 (runs ros core through the rosbridge (web socket package) launch file):

cd catkin_ws
source devel/setup.bash
roslaunch rosbridge_server rosbridge_websocket.launch

#### Terminal 2 (runs the package I made that listens to /score topic which uses std_msgs/Int64 messages):
cd catkin_ws
source devel/setup.bash
rosrun listener_package score_listener

#### Terminal 3 (runs the web app):
cd webapp
npm install
npm run dev

#### Web Browser:
http://localhost:3000 -->
