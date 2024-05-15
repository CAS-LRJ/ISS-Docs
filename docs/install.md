---
title: Install
layout: home
nav_order: 1
---
# ISS

Intelligent Self-driving System (ISS) is a modular framework written in Python and C++ with the aim to build an extensible workspace tailored to research. This framework will contain both traditional and deep learning algorithms for self-driving related tasks such as perception, localization, mapping, prediction, planning, and control. The modular design with minimal dependency on external libraries can provide a transparent and clean workspace for researchers to evaluate algorithms for autonomous driving systems.

The code of ISS can be downloaded from its [*Github Repository*](https://github.com/CAS-LRJ/ISS), where detailed installation instructions can be found.

## Pre-requisites

ISS is tested with Ubuntu 20.04, running Python 3.8.

For those interested in using ISS in conjunction with Gazebo and ROS-Noetic, you should install [ROS-Noetic](https://wiki.ros.org/noetic/Installation), following the instructions provided in the official ROS documentation.

To utilize ISS with CARLA, it is necessary to install CARLA. We recommend using version 0.9.13, which can be found at the [CARLA](https://github.com/carla-simulator/carla/releases) GitHub releases page.


## Development Version
To install the development version of ISS, please follow the instructions below.
```
git clone https://github.com/CAS-LRJ/ISS.git
cd ISS && python3 setup.py develop
```

We also provided a docker image with necessary dependencies installed, with Kasm Workspaces so that you can run ISS in the server and access it from your browser. To get access the docker image and init bash script, see [ISS_Docker](https://tis.ios.ac.cn/tisfiles/iss_docker/) for more information. 

## Build
To build the ROS package of ISS, please follow the instructions below.
```
cd ISS/ros1_ws && catkin build
source devel/setup.bash
```

## Run tasks
If using Gazebo, simply do:
```
roslaunch robot_gazebo gazebo_demo.launch
```

If using CARLA, please launch CARLA first, then do:
```
roslaunch carla_bridge carla_demo.launch
```