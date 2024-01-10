---
title: Control
layout: home
nav_order: 4
math: mathjax
parent: Algorithms

---

# Control
## Introduction to the Control Module
The Control module is responsible for generating control commands to steer the vehicle and maintain its desired trajectory. <a href="#ref1"><sup>[1]</sup></a>
In this documentation, we outline our current methodologies, from the simple [PID controller](#PID) to the more advanced [Model Predictive Control (MPC)](#MPC).


## PID Controller for Waypoint Tracking<a name="PID"/>

### Overview:
The PID controller is one of the fundamental control algorithms in our autonomous driving pipeline. 
It continuously calculates an "error" value as the difference between a desired setpoint (in this case, waypoints) and the current vehicle position.

### Components:
The PID controller include three components, as its name suggests:
- **Proportional (P)**: provides a control output to correct the current position error.
- **Integral (I)**: Corrects the accumulation of past errors.
- **Derivative (D)**: predicts and counters the future error trend based on its current rate of change.

### Application:
We use the PID controller primarily for waypoint tracking, maintaining lane position, and ensuring the vehicle follows a predefined path with minimal deviation.


## Model Predictive Control (MPC) for Trajectory Tracking<a name="MPC"/>

### Overview:
Model Predictive Control (MPC) <a href="#ref2"><sup>[2]</sup></a>  is an advanced control technique that uses a model of the vehicle's dynamics to predict its future states over a defined horizon. 
At each time step, the MPC algorithm solves an optimization problem to find the optimal control inputs, considering vehicle dynamics, constraints, and the desired trajectory.

### Key Features:
The MPC controller involves three key features to decide what actions to perform to control the vehicle's movement:
- **Prediction Model**: predicts future states of the vehicle based on its current state and potential control inputs.
- **Optimization**: continuously solves an optimization problem to determine the best control actions over the prediction horizon.
- **Receding Horizon Strategy**: implements only the first control action of the optimized sequence and re-evaluates at the next time step, adapting to changing conditions.

### Application:
The MPC controller will be instrumental in scenarios where precise trajectory tracking is essential, especially in complex driving environments with dynamic obstacles, tight curves, and varying road conditions. 
By anticipating future states and constraints, MPC offers enhanced path following accuracy and robustness compared to traditional controllers.

## Implementation Roadmap:
1. Maintain and fine-tune the existing PID controller to ensure basic waypoint tracking functionality.
2. Develop a mathematical model representing the vehicle's dynamics.
3. Integrate optimization solvers compatible with our system architecture for MPC.
4. Design and implement the MPC framework, ensuring it considers vehicle constraints.
5. Test the MPC in simulation for various scenarios and refine the model and controller parameters.
6. Gradually deploy and evaluate the MPC in real-world tests, starting with low-complexity environments and escalating to more challenging scenarios.

## References
<ol>
    <li id="ref1">Paden, Brian, et al. "A survey of motion planning and control techniques for self-driving urban vehicles." IEEE Transactions on intelligent vehicles 1.1 (2016): 33-55.</li>
    <li id="ref2">Rajamani, Rajesh. "Vehicle dynamics and control." Springer Science & Business Media, 2011.</li>
</ol>