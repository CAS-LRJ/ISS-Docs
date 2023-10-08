---
title: Reinforcement Learning
layout: home
nav_order: 9
---

# Deep Reinforcement Learning

Deep Reinforcement Learning (DRL) is an area of machine learning that focuses on training agents to make sequences of decisions by interacting with an environment. The agent seeks to learn the best strategy, or policy, to achieve the maximum cumulative reward over time. DRL has shown impressive results in various domains, from game playing to robotic control.

![RL_pipeline](../../assets/RL_pipeline.png){: .center-image width="70%"}

*Reinforcement Learning Pipeline*
{: .text-center}

## Our Plan

### 1. Problem Formulation
Define the specific navigation tasks we want the robot to accomplish such as waypoint following, obstacle avoidance, etc. We will then set up the reward structure to encourage these desired behaviors.

### 2. Simulator Setup
We will be using an appropriate simulator for Ackermann robots, possibly Gazebo, Webots, or even a custom simulator. The goal is to model the robot's dynamics and sensory inputs as accurately as possible.

### 3. Baseline DRL Algorithm Selection
Our starting point will be popular reinforcement learning algorithms like Proximal Policy Optimization (PPO), Deep Q-Network (DQN), or Twin Delayed Deep Deterministic Policy Gradient (TD3).

We are going to use [Stable Baselines3](https://github.com/DLR-RM/stable-baselines3) for our DRL algorithms. Stable Baselines3 is a set of improved implementations of reinforcement learning algorithms in PyTorch.

### 4. Training in Simulation
Starting with a basic environment (few obstacles, clear paths), we will progress to more intricate scenarios. We will monitor the agent's training progress and tune hyperparameters for optimal performance. A few simulators we are considering are listed below:


| **Simulator**        | **Strengths**                                                                   | **Weaknesses**                                   |
|----------------------|---------------------------------------------------------------------------------|--------------------------------------------------|
| **Gazebo (ROS)**     | - Easy sim-to-real experiments. <br> - Integrates well with the ROS ecosystem.  | - Slow simulation speeds. <br> - Requires proficiency in ROS. |
| **Isaac Sim (NVIDIA)** | - GPU acceleration for fast training. <br> - High-quality graphics.            | - Steeper learning curve. <br> - May require advanced hardware. |
| **Carla**            | - Complex sensor data. <br> - Real vehicle physics.                             | - Slow simulations. <br> - High computational resource needs. |
| **SMARTS (Huawei)**  | - Great visualization. <br> - Broad action space for RL in driving.             | - Might be challenging for newcomers. <br> - Specific environment understanding required. |


### 5. Transfer Learning and Domain Adaptation
Given the known challenges of the sim-to-real gap, we will implement techniques like domain randomization in the simulator and consider fine-tuning on the real robot.

### 6. Safety Precautions
Safety is paramount. When transitioning to a real robot, we'll ensure protocols are in place to protect both the robot and its surroundings.

### 7. Evaluation
We will set up evaluation metrics to gauge the performance of our agent in real-world settings, comparing different algorithms to identify the most suitable one.

### 8. Iterate and Improve
Using feedback from real-world testing, we'll refine our simulation, reward designs, and DRL algorithms to continually enhance performance.

