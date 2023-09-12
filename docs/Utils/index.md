---
title: Utilities
layout: home
nav_order: 9
---

Classes that provide necessary definition and transformation functions and classes for the project. In particular, definition of cubic spline, geometry types of CARLA and functions of coordinate transformation, type conversion are now being provided. In progress.

## DataExchange

Classes of data which ISS uses to convey information between different modules.

### Control

#### `VehicleControl`

Helper class to load/store vehicle control data.

##### Instance variables

- `steer(float)`: steer level
- `throttle(float)`: throttle level
- `brake(float)`: brake level
- `hand_brake(bool)`: using hand brake or not
- `manual_gear_shift(bool)`: using manual gear shift or not

##### Methods

- `__init__(self, steer = 0., throttle=0., brake=1., hand_brake=True, manual_gear_shift=False)`
    - Parameters:
        - `steer(float)`
        - `throttle(float)`
        - `brake(float)`
        - `hand_brake(bool)`
        - `manual_gear_shift(bool)`

### Localization

#### `VehicleTransform`

Helper class to load/store vehicle localization data.

##### Instance variables

- `x,y,z(float, float, float)`: location in global coordinate system
- `velocity_{x,y,z}(float, float, float)`: vehicle velocity in three orthogonal directions
- `velocity(float)`: vehicle velocity
- `acceleration_{x,y,z}(float, float, float)`: vehicle acceleration in three orthogonal directions
- `acceleration(float)`: vehicle acceleration
- `yaw, pitch, roll(float, float, float)`: rotation in global coordinate system

##### Methods

- `__init__(self, location = (None, None, None), velocity = (None, None, None, None), acceleration = (None, None, None, None), rotatation = (None, None, None))`
    - Parameters:
        - `location(tuple(float, float, float))`
        - `velocity(tuple(float, float, float, float))`
        - `acceleration(tuple(float, float, float, float))`
        - `rotation(tuple(float, float, float))`

### Perception

#### `ObjectDetectionOutput`

Helper class to load/store perception data of object detection task.

##### Instance Variable

- `_label(string)`: object label
- `_score(float)`: confidence score
- `_bbox(Boundingbox)`: detected bounding box of the object

##### Methods

- `__init__(self)`
    - Parameters:
        - `label(string)`
        - `score(float)`
        - `bbox(Boundingbox)`

### Planning

#### `Trajectory`

Helper class to load/store trajectory data of planning module.

##### Instance Variable

- `waypoints(list(tuple(float, float, float)))`: waypoints of the trajectory, waypoint is consist of x, y and yaw.
- `speed(list(float))`: list of every speed of the corresponding waypoint

##### Methods

- `__init__(self, waypoints, speed)`
    - Parameters:
        - `waypoints(list(tuple(float, float, float)))`
        - `speed(list(float))`

- `downsample(self, precision=0.1)`
    
    Drop certain proportion of the waypoints.
    - Parameters:
        - `precision(float)`
### Sensor

#### `CameraOutput`

Helper class to load/store camera data from source sensor.

##### Instance Variable

- `intrinsic(np.ndarray(4,4))`: intrinsic parameter of the camera
- `image(np.ndarray(h,w,3))`: captured image

##### Methods

- `__init__(self, intrinsic, image)`
    - Paramters:
        - `intrinsic(np.ndarray(4,4))`
        - `image(np.ndarray(h,w,3))`

#### `LiDAROutput` and `LiDARSegOutput`

Helper class to load/store LiDAR data (with segmentation information) from source sensor.

##### Instance Variable

- `points(list(Point))`: point clout

##### Methods

- `__init__(self, points)`
    - Parameters:
        - `points(list(Point))`

#### `RadarOutput`

Helper class to load/store Radar data from source sensor.

##### Instance Variable


- `points(list(Point))`: point clout

##### Methods

- `__init__(self, points)`
    - Parameters:
        - `points(list(Point))`

## MathUtils

Classes and functions that are used to proceed mathematical operations.

### Angle

- `pi_2_pi(angle)`: normalize angle range into $[-\pi, \pi]$

- `zero_2_2pi(angle)`: normalize angle range into $[0, 2\pi]$

- `calculate_rot_angle(dir)`: convert a rotation matrix into an angle

### Cubic Spline
{: .d-inline-block }

(WIP)
{: .label .label-blue}

### Quartic/Quintic Polynomial
{: .d-inline-block }

(WIP)
{: .label .label-blue}

## SensorUtils

Classes and functions of spatial information and its convertion with the corresponding data structures in various simulators.

- `Location`

- `Rotation`

- `Transform`

- `BoundingBox`



## VehicleUtils
