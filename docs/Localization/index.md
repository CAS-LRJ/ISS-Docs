---
title: Localization
layout: home
nav_order: 4
---

# Localization
## Introduction to the Localization Module

The localization module ensures that the autonomous vehicle not only understand its position in the vast tapestry of roads and environments but do so with unparalleled accuracy. In this documentation, we outline our current pipeline, from the individual sensors to the sensor fusion algorithms.

## Individual Sensor

To achieve precise localization, a multifaceted approach using various sensors and algorithms is adopted:

1. **Lidar**:
   - **Iterative Closest Point (ICP)** <a href="#ref1"><sup>[1]</sup></a>: This algorithm aligns two point clouds to determine the best-fit transform that aligns them.
   - **Normal Distributions Transform (NDT)** <a href="#ref2"><sup>[2]</sup></a>: This advanced method represents point cloud data using normal distributions, offering a robust and efficient means of registration.

2. **IMU (Inertial Measurement Unit)**:
   - **Dead Reckoning**: By leveraging motion sensor data, dead reckoning provides a continuous estimate of the vehicle's position. However, its accuracy diminishes over extended periods and requires supplementary data for correction.

3. **GPS (Global Positioning System)**:
   - While GPS offers a global reference for positioning, its precision may not be sufficient for the tight tolerances of autonomous driving. Thus, GPS data is often fused with other sensor data to enhance accuracy.

## Sensor Fusion

The key to impeccable localization is not just in the individual prowess of sensors, but in their collaborative strength:

1. **Filter-based Methods**:
   - Recursive algorithms, such as the **Kalman Filter** and **Particle Filter** <a href="#ref3"><sup>[3]</sup></a>, are indispensable for real-time state estimation and prediction.

2. **Optimization-based Methods**:
   - Holistic approaches like **GraphSLAM** <a href="#ref4"><sup>[4]</sup></a> adjust and refine entire trajectories or maps, ensuring the highest accuracy in post-processing scenarios.

## Implementation Roadmap
1. Maintain Lidar (ICP, NDT), IMU (Dead Reckoning), GPS, and filter-based fusion.
2. Study optimization-based fusion: GraphSLAM, Bundle Adjustment, Pose Graph Optimization.
3. Gather and process datasets for optimization methods.
4. Integrate optimization-based fusion into the current pipeline.

## References
<ol>
    <li id="ref1">Besl P J, McKay N D. Method for registration of 3-D shapes[C]//Sensor fusion IV: control paradigms and data structures. Spie, 1992, 1611: 586-606.</li>
    <li id="ref2">Biber P, Straßer W. The normal distributions transform: A new approach to laser scan matching[C]//Proceedings 2003 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS 2003)(Cat. No. 03CH37453). IEEE, 2003, 3: 2743-2748.</li>
    <li id="ref3">Thrun S. Probabilistic robotics[J]. Communications of the ACM, 2002, 45(3): 52-57.</li>
    <li id="ref4">Shan T, Englot B, Meyers D, et al. Lio-sam: Tightly-coupled lidar inertial odometry via smoothing and mapping[C]//2020 IEEE/RSJ international conference on intelligent robots and systems (IROS). IEEE, 2020: 5135-5142.</li>
</ol>

