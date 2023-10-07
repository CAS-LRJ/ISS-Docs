---
title: Planning
layout: home
nav_order: 6
has_children: true
---


## Introduction
The autonomous driving pipeline encompasses a multitude of components, from perception to control. Central to this pipeline is the "Planning Module," responsible for making strategic and tactical decisions about the vehicle's movement. This module breaks down into three key stages: Route Planning, Behavior Planning, and Motion Planning. In this post, we'll explore each stage in-depth.

## 1. Route Planning

### Objective
To plot the most effective course from the current location to the desired endpoint, much like how conventional GPS systems operate.

### Inputs
- Start and endpoint coordinates
- Road network topology
- Traffic conditions
- Permanent obstacles

### Outputs
A path or a series of waypoints bridging the start and destination, while sidestepping any permanent obstacles.

### Challenges
- Adapting to changing road situations
- Incorporating real-time traffic details
- Ensuring the chosen route is both safe and efficient

## 2. Behavior Planning

### Objective
To dictate the vehicle's overarching behavior, from decisions about lane switches, overtaking, yielding, to making turns.

### Inputs
- Designated route
- Data about neighboring vehicles and pedestrians (sourced from LIDAR, radar, cameras, etc.)
- Traffic light information
- Other pertinent environmental data

### Outputs
Macro-level directives like "shift to the left lane", "trail the vehicle in front", or "get ready to turn right".

### Challenges
- Anticipating the intentions and forthcoming actions of surrounding drivers and pedestrians
- Safe decision formulation in intricate scenarios
- Navigating uncommon edge cases

## 3. Motion Planning

### Objective
To chart a trajectory that's both safe and consistent for the vehicle, reflecting the behavior objectives and staying within the vehicle's dynamic and kinematic constraints.

### Inputs
- Intended behavior
- Present vehicle state (such as position, speed, and acceleration)
- Road map details
- Dynamic obstruction data

### Outputs
A nuanced trajectory, detailing the vehicle's position, speed, and acceleration over a specified time frame.

### Challenges
- Crafting trajectories that avoid collisions and are streamlined
- Managing uncertain data from sensors
- Real-time trajectory mapping
