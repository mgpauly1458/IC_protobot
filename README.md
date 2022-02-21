# IC_protobot

## Overview

This is a clone of the shared project repository made by the members of the University of Hawaii Robotic Space Exploration Team(link). Our team's goal is to creat a six wheeled robot that can drive, operate a manipulator arm, detect life, and autonomously navigate which we will officially enter into the University Rover Challenge(link), June 2022. This repository contains the software module prototypes which we worked diligently on in order to prove the architectural concepts laid out in our Critical Design Review(link).

Contributors: Maxwell Pauly, Bret Witt, Ashten Akemoto, Jacob Sequeira, Jeraldine Milla, Stephanie Alemore, and Zolbo Tomita

## Web App Graphical User Interface

https://user-images.githubusercontent.com/74911365/140019513-80895195-2fa0-49e1-8030-edcdf03711ba.mp4

## Dependencies
### sudo apt update
### sudo apt upgrade
### sudo apt-get install ros-noetic-rosbridge-suite
### sudo apt-get install ros-noetic-rosbridge-server
### sudo apt install nodejs npm


## To get it to work:

### Terminal 1 (runs ros core through the rosbridge (web socket package) launch file):

cd catkin_ws
source devel/setup.bash
roslaunch rosbridge_server rosbridge_websocket.launch

### Terminal 2 (runs the package I made that listens to /score topic which uses std_msgs/Int64 messages):
cd catkin_ws
source devel/setup.bash
rosrun listener_package score_listener

### Terminal 3 (runs the web app):
cd webapp
npm install
npm run dev

### Web Browser:
http://localhost:8000
