---
title: Prediction
layout: home
nav_order: 8
math: katex
---

# Prediction

## Introduction to the Prediction Module

Prediction plays a pivotal role in autonomous driving, determining the probable actions of on-road agents to ensure safe navigation. In this documentation, we outline our current methodologies, from the simple constant velocity motion predictor to the more advanced Motion Transformer.

## 1. Constant Velocity Motion Predictor

### Overview
The constant velocity model is the most basic but effective method of prediction <a href="#ref1"><sup>[1]</sup></a>, assuming an entity continues its current trajectory at a constant speed. Here, we forward simulate the kinematic bicycle model via Runge-Kutta 4 (RK4) integration, assuming no acceleration and steering angle.


### Applicability and Limitations
- **Applicability**: Ideal for high-speed highways where motion is relatively linear.
- **Limitations**: In urban or crowded areas, this model may not capture erratic movements of agents.

### Mathematical Model
The primary equations governing the kinematic bicycle model are:

<figure>
    <img src="/assets/kine_bicycle_model.png" alt="kine_bicycle_model" style="width: 70%;">
    <figcaption>Kinematic bicycle model</figcaption>
</figure>

1. **Position updates**:
   
    $$ x(t+1) = x(t) + v(t) \cos(\theta(t)) \Delta t $$

    $$ y(t+1) = y(t) + v(t) \sin(\theta(t)) \Delta t $$

2. **Heading update**:
   
    $$ \theta(t+1) = \theta(t) + \frac{v(t)}{l_{wb}} \tan(\delta) \Delta t $$

Where:
- $$ (x, y) $$ represents the vehicle's position.
- $$ \theta $$ is the vehicle's heading.
- $$ v $$ is the vehicle's velocity.
- $$ \delta $$ is the steering angle at the front wheel.
- $$ l_{wb} $$ is the wheelbase, or distance between front and rear axles.
- $$ \Delta t $$ is the time step.


The RK4 method is then applied for forward simulation to improve prediction accuracy over short horizons.


### Sample Use Cases
- Highways and expressways.
- Open areas with minimal obstructions.

## 2. Motion Transformer

### Overview
The Motion Transformer is a state-of-the-art model that considers historical data to predict future trajectories.

<figure>
    <img src="/assets/motion_transformer.png" alt="Motion Transformer">
    <figcaption>The structure of the motion transformer<a href="#ref2"><sup>[2]</sup></a></figcaption>
</figure>

### Why Motion Transformer?
Simpler models lack the nuance needed for complex environments. The Motion Transformer accounts for historical trajectories, giving it an edge in intricate scenarios.

### Architecture & Components
- **Attention Mechanisms**: To weigh the importance of different historical data points.
- **Encoder-Decoder Structures**: The encoder processes the input sequence, while the decoder produces the predicted trajectory.

### Input/Output Details
- **Input**: Historical trajectory data.
- **Output**: Predicted future trajectories with confidence intervals.

## Implementation Roadmap
1. Maintain the existing constant velocity motion predictor to ensure basic functionality.
2. Understand and set up the Motion Transformer's neural network.
3. Collect, process datasets, and conduct training and simulation tests.
4. Integrate into the current pipeline and ensure ongoing model optimization.

## References
<ol>
    <li id="ref1">Schöller C, Aravantinos V, Lay F, et al. What the constant velocity model can teach us about pedestrian motion prediction[J]. IEEE Robotics and Automation Letters, 2020, 5(2): 1696-1703.</li>
    <li id="ref2">Shi S, Jiang L, Dai D, et al. Motion transformer with global intention localization and local movement refinement[J]. Advances in Neural Information Processing Systems, 2022, 35: 6531-6543.</li>
</ol>