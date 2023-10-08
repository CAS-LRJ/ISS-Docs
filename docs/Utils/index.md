---
title: Utilities
layout: home
nav_order: 9
---

Classes that provide necessary definition and transformation functions and classes for the project. In particular, definition of cubic spline, geometry types of CARLA and functions of coordinate transformation, type conversion are now being provided. In progress.

# DataExchange <a name="DataExchange"></a> (_dir_)

Classes of data which ISS uses to convey information between different modules. And _dir_ means directory.



### VehicleControl <a name="VehicleControl"></a> (_class_)

Helper class to load/store vehicle control data. Manages the basic movement of a vehicle using typical driving controls.

#### Instance Variables
- <a name="VehicleControl.steer"></a>**<font color="#f8805a">steer</font>** (_float_)   
   Steer level. A scalar value to control the vehicle steering [-1.0, 1.0]. Default is 0.0.
- <a name="VehicleControl.throttle"></a>**<font color="#f8805a">throttle</font>** (_float_)   
   Throttle level. A scalar value to control the vehicle throttle [0.0, 1.0]. Default is 0.0.
- <a name="VehicleControl.brake"></a>**<font color="#f8805a">brake</font>** (_float_)   
   Brake level. A scalar value to control the vehicle brake [0.0, 1.0]. Default is 0.0.
- <a name="VehicleControl.hand_brake"></a>**<font color="#f8805a">throttle</font>** (_float_)   
   Using hand brake or not. Determines whether hand brake will be used. Default is False.
- <a name="VehicleControl.manual_gear_shift"></a>**<font color="#f8805a">throttle</font>** (_float_)   
   Using manual gear shift or not. Determines whether the vehicle will be controlled by changing gears manually. Default is False.

#### Methods
- <a name="VehicleControl.__init__"></a>**<font color="#7fb800">\_\_init\_\_</font>**(<font color="#00a6ed">**self**, **steer** = 0., **throttle**=0., **brake**=1., **hand_brake**=True, **manual_gear_shift**=False</font>)  
Initialize instance variables with parameters.
  - **Parameters:**
    - `steer`(_float_)
    - `throttle`(_float_)
    - `brake`(_float_)
    - `hand_brake`(_bool_)
    - `manual_gear_shift`(_bool_) 



## Localization <a name="Localization"></a> (_dir_)
Classes that provide necessary defination and methods for  **<span style="color:#ADD8E6">Localization</span>** modular.

### VehicleTransform <a name="VehicleTransform"></a> (_class_)

Helper class to load/store vehicle localization data. Manages the basic data transform.

#### Instance Variables
- <a name="VehicleTransform.x"></a>**<font color="#f8805a">x</font>** (_float<small>- meters</small>_)   
   X-axis of Cartesian location in global coordinate system.
- <a name="VehicleTransform.y"></a>**<font color="#f8805a">y</font>** (_float<small>- meters</small>_)   
   Y-axis of Cartesian location in global coordinate system.
- <a name="VehicleTransform.z"></a>**<font color="#f8805a">z</font>** (_float<small>- meters</small>_)   
   Z-axis of Cartesian location in global coordinate system.
- <a name="VehicleTransform.velocity_x"></a>**<font color="#f8805a">velocity_x</font>** (_float<small>- m/s</small>_)   
   Vehicle's X-axis velocity.
- <a name="VehicleTransform.velocity_y"></a>**<font color="#f8805a">velocity_y</font>** (_float<small>- m/s</small>_)   
   Vehicle's Y-axis velocity.
- <a name="VehicleTransform.velocity_z"></a>**<font color="#f8805a">velocity_z</font>** (_float<small>- m/s</small>_)   
   Vehicle's Z-axis velocity.
- <a name="VehicleTransform.acceleration"></a>**<font color="#f8805a">acceleration</font>** (_list(float<small>- m/s<sup>2</sup></small>)_)   
   Vehicle's  acceleration.
- <a name="VehicleTransform.acceleration_x"></a>**<font color="#f8805a">acceleration_x</font>** (_float<small>- m/s<sup>2</sup></small>_)   
   X-axis of Vehicle's  acceleration.
- <a name="VehicleTransform.acceleration_y"></a>**<font color="#f8805a">acceleration_y</font>** (_float<small>- m/s<sup>2</sup></small>_)   
   Y-axis of Vehicle's  acceleration.
- <a name="VehicleTransform.acceleration_z"></a>**<font color="#f8805a">acceleration_z</font>** (_float<small>- m/s<sup>2</sup></small>_)   
   Z-axis of Vehicle's  acceleration.
- <a name="VehicleTransform.roll"></a>**<font color="#f8805a">roll</font>** (_float_)   
   X-axis rotation angle in global coordinate system.
- <a name="VehicleTransform.pitch"></a>**<font color="#f8805a">pitch</font>** (_float_)   
   Z-axis rotation angle in global coordinate system.
- <a name="VehicleTransform.yaw"></a>**<font color="#f8805a">yaw</font>** (_float_)   
   Z-axis rotation angle in global coordinate system.

#### Methods
- <a name="VehicleTransform.__init__"></a>**<font color="#7fb800">\_\_init\_\_</font>**(<font color="#00a6ed">**self**, **location**=(None, None, None), **velocity**=(None, None, None, None), **acceleration**=(None, None, None, None), **rotatation**=(None, None, None)</font>)  
Initialize instance variables with parameters. Most parameters default as **None**.
  - **Parameters:**
    - `location`(_tuple(float, float, float)_)
    - `velocity`(_tuple(float, float, float, float)_)
    - `acceleration`(_tuple(float, float, float, float)_)
    - `rotation`(_tuple(float, float, float)_)



## Perception <a name="Perception"></a> (_dir_)
Classes that provide necessary defination and methods for  **<span style="color:#ADD8E6">Perception</span>** modular.

### ObjectDetectionOutput <a name="ObjectDetectionOutput"></a> (_class_)
Helper class to load/store perception data of object detection task.

#### Instance Variables
- <a name="ObjectDetectionOutput._label"></a>**<font color="#f8805a">_label</font>** (_string_)   
   Object detected label. Initialize as **None**.
- <a name="ObjectDetectionOutput._score"></a>**<font color="#f8805a">_score</font>** (_string_)   
   Object detected confidence score. Initialize as **None**.
- <a name="ObjectDetectionOutput._bbox"></a>**<font color="#f8805a">_bbox</font>** (_string_)   
   Object detected bounding box. Initialize as **None**.



#### Methods
- <a name="ObjectDetectionOutput.__init__"></a>**<font color="#7fb800">\_\_init\_\_</font>**(<font color="#00a6ed">**self**</font>)  
Initialize instance variables with parameters. Most parameters default as **None**.
  - **Parameters:**
    - `location`(_tuple(float, float, float)_)
    - `velocity`(_tuple(float, float, float, float)_)
    - `acceleration`(_tuple(float, float, float, float)_)
    - `rotation`(_tuple(float, float, float)_)
- <a name="ObjectDetectionOutput.get_state_bicycle_model"></a>**<font color="#7fb800">get_state_bicycle_model</font>**(<font color="#00a6ed">**self**</font>)  
Get bicycle obstacles' information, such as location, rotation, etc.
   - **Return:** _[numpy.array([x, y, yaw, vel])]()_ - where x, y stand for X-axis Y-axis of Cartesian location, yaw is Z-axis rotation angle, vel is velocity of Real number.
- <a name="ObjectDetectionOutput.get_veh_info"></a>**<font color="#7fb800">get_veh_info</font>**(<font color="#00a6ed">**self**</font>)  
Get vehicle obstacles' information, such as bounding box, etc.
   - **Return:** _[veh_info]()_ - including: length, width, wheelbase, overhang_rear, overhang_front.




## Planning <a name="Planning"></a> (_dir_)

### Trajectory <a name="Trajectory"></a> (_class_)
Helper class to load/store trajectory data of planning module.

##### Instance Variable
- <a name="Trajectory.waypoints"></a>**<font color="#f8805a">waypoints</font>** (_list(tuple(float, float, float))_)   
   Waypoints of the trajectory. Waypoint is consist of x, y and yaw.
- <a name="Trajectory.speed"></a>**<font color="#f8805a">speed</font>** (_list(float)_)   
   list of every speed of the corresponding waypoint.

##### Methods
- <a name="Trajectory.__init__"></a>**<font color="#7fb800">\_\_init\_\_</font>**(<font color="#00a6ed">**self**, **waypoints**, **speed**</font>)  
Initialize instance variables with parameters. 
  - **Parameters:**
    - `waypoints`(_list(tuple(float, float, float))_) 
    - `speed`(_list(float)_)
- <a name="Trajectory.downsample"></a>**<font color="#7fb800">downsample</font>**(<font color="#00a6ed">**self**, **precision**=0.1</font>)  
Drop certain proportion of the waypoints.
  - **Parameters:**
    - `precision`(_float_) 

### AllPredictionOutput <a name="AllPredictionOutput"></a> (_class_)
<blockquote><strong><em><font color="#ff0000"> To Be Accomplished</font></em></strong></blockquote>

### TrajectoryPredictionOutput <a name="TrajectoryPredictionOutput"></a> (_class_)
<blockquote><strong><em><font color="#ff0000"> To Be Accomplished</font></em></strong></blockquote>



## Sensor <a name="Sensor"></a> (_dir_)

### CameraOutput <a name="CameraOutput"></a> (_class_)
Helper class to load/store camera data from source sensor.

##### Instance Variable
- <a name="CameraOutput.intrinsic"></a>**<font color="#f8805a">intrinsic</font>** (_np.ndarray(4,4)_)   
   Intrinsic parameter of the camera.
- <a name="CameraOutput.image"></a>**<font color="#f8805a">image</font>** (_np.ndarray(h,w,3)_)   
   Captured image.

##### Methods
- <a name="CameraOutput.__init__"></a>**<font color="#7fb800">\_\_init\_\_</font>**(<font color="#00a6ed">**self**, **intrinsic**, **image**</font>)  
Initialize instance variables with parameters. 
  - **Parameters:**
    - `intrinsic` (_np.ndarray(4,4)_)  
    - `image` (_np.ndarray(h,w,3)_) 


### LiDAROutput <a name="LiDAROutput"></a> (_class_)
Helper class to load/store LiDAR data (with segmentation information) from source sensor.

##### Instance Variable
- <a name="LiDAROutput.points"></a>**<font color="#f8805a">points</font>** (_list(Point)_)   
   Points of point cloud.

##### Methods
- <a name="LiDAROutput.__init__"></a>**<font color="#7fb800">\_\_init\_\_</font>**(<font color="#00a6ed">**self**</font>)  
Initialize instance variables with parameters. 
  - **Parameters:**
    - `points` (_list(Point)_)  

### LiDARSegOutput <a name="LiDARSegOutput"></a> (_class_)
Helper class to load/store LiDAR data (with segmentation information) from source sensor.

##### Instance Variable
- <a name="LiDARSegOutput.points"></a>**<font color="#f8805a">points</font>** (_list(Point)_)   
   Points of point cloud.

##### Methods
- <a name="LiDARSegOutput.__init__"></a>**<font color="#7fb800">\_\_init\_\_</font>**(<font color="#00a6ed">**self**</font>)  
Initialize instance variables with parameters. 
  - **Parameters:**
    - `points` (_list(Point)_)  


### Detection2DInput <a name="Detection2DInput"></a> (_class_)
<blockquote><strong><em><font color="#ff0000"> To Be Accomplished</font></em></strong></blockquote>

### Detection2DOutput <a name="Detection2DOutput"></a> (_class_)
<blockquote><strong><em><font color="#ff0000"> To Be Accomplished</font></em></strong></blockquote>


## MathUtils<a name="MathUtils"></a> (_class_)
Classes and functions that are used to proceed mathematical operations.

### Angle <a name="Angle"></a> (_file_)
Helper methods for deal with angle data.

##### Methods
- <a name="pi_2_pi"></a>**<font color="#7fb800">pi_2_pi</font>**(<font color="#00a6ed">**angle**</font>)  
Normalize angle range into $[-\pi, \pi]$
  - **Parameters:**
    - `angle` (_float<small>-radians</small>_)
  - **Return:** _[angle]()_(_float_) -which value is $[-\pi, \pi]$
- <a name="zero_2_2pi"></a>**<font color="#7fb800">zero_2_2pi</font>**(<font color="#00a6ed">**angle**</font>)  
Normalize angle range into $[0, 2\pi]$
  - **Parameters:**
    - `angle` (_float<small>-radians</small>_)  
  - **Return:** _[angle]()_(_float_) -which value is $[0, 2\pi]$
- <a name="calculate_rot_angle"></a>**<font color="#7fb800">calculate_rot_angle</font>**(<font color="#00a6ed">**angle**</font>)  
Convert a rotation matrix into an angle.
  - **Parameters:**
    - `dir` (_numpy.array([[float, float, float]])<small>-meters</small>_) - means direction vectors.
  - **Return:** _[rot_angle]()_(_numpy.array([[float]])_) -which value is $[0, 2\pi]$


### Spline <a name="Spline"></a> (_class_)
1D(one demension) Cubic spline class. Cubic spline interpolation is a method of smoothly interpolating between multiple data points when given multiple data points. 
In this class, some method is provided to get interpolating function and caculate input first/second/third derivative.
This class can be the foundation of class Spline2D. It can be not only used in Cartesian coordinate, but also Frenet coordinate.  
In mathematical, Cubic Spline is define as $y = a_i + b_i * x + c_i * x^2 + d_i * x^3$, where $i \in [0, nx]$ and nx is defined as demension of $x$.

##### Usage
To create a **<span style="color:#ADD8E6">Spline</span>** object, you need to provide a set of x-coordinate and y-coordinate points. 
For example:
```py
x = [0.0, 1.0, 2.0, 3.0, 4.0]
y = [0.0, 1.0, 0.0, -1.0, -2.0]

spline = Spline(x, y)
```

##### Instance Variable
- <a name="Spline.x"></a>**<font color="#f8805a">x</font>** (_list[float]_)   
A list of X-coordinate points.
- <a name="Spline.y"></a>**<font color="#f8805a">y</font>** (_list[float]_)   
A list of Y-coordinate points.
- <a name="Spline.nx"></a>**<font color="#f8805a">nx</font>** (_list[float]_)   
Demension of **x**.
- <a name="Spline.a"></a>**<font color="#f8805a">a</font>** (_list[float]_)   
Coefficient of the zeroth-degree term in Cubic Spine function.
- <a name="Spline.b"></a>**<font color="#f8805a">b</font>** (_list[float]_)   
Coefficient of the first-degree term in Cubic Spine function.
- <a name="Spline.c"></a>**<font color="#f8805a">c</font>** (_list[float]_)   
Coefficient of the second-degree term in Cubic Spine function.
- <a name="Spline.d"></a>**<font color="#f8805a">d</font>** (_list[float]_)   
Coefficient of the third-degree term in Cubic Spine function.


##### Methods
- <a name="Spline.__init__"></a>**<font color="#7fb800">\_\_init__</font>**(<font color="#00a6ed">**self**, **x**, **y**</font>)  
Generate Cubic Spline function with input x and y which means caculating the Coeeficient of polynomial.
  - **Parameters:**
    - `x` (_list[float]_)
    - `y` (_list[float]_)
- <a name="Spline.calc"></a>**<font color="#7fb800">calc</font>**(<font color="#00a6ed">**self**, **t**</font>)  
Calc $y$ position for given $t$ by generated Cubic Spline function.
  - **Parameters:**
    - `t` (_float_) - where $t$ is $x$ metion above.
  - **Return:** _[result]()_(_float_) - where $result$ is $y$ metion above.
- <a name="Spline.calcd"></a>**<font color="#7fb800">calcd</font>**(<font color="#00a6ed">**self**, **t**</font>)  
Calc $y'$ position for given $t$ by generated Cubic Spline function, where $y'$ deined as first deriviate of $y$.
  - **Parameters:**
    - `t` (_float_) - where $t$ is $x$ metion above.
  - **Return:** _[result]()_(_float_) - where $result$ is $y'$.
- <a name="Spline.calcdd"></a>**<font color="#7fb800">calcdd</font>**(<font color="#00a6ed">**self**, **t**</font>)  
Calc $y''$ position for given $t$ by generated Cubic Spline function, where $y''$ deined as second deriviate of $y$.
  - **Parameters:**
    - `t` (_float_) - where $t$ is $x$ metion above.
  - **Return:** _[result]()_(_float_) - where $result$ is $y''$.
- <a name="Spline.calcddd"></a>**<font color="#7fb800">calcddd</font>**(<font color="#00a6ed">**self**, **t**</font>)  
Calc $y'''$ position for given $t$ by generated Cubic Spline function, where $y'''$ deined as first deriviate of $y$.
  - **Parameters:**
    - `t` (_float_) - where $t$ is $x$ metion above.
  - **Return:** _[result]()_(_float_) - where $result$ is $y'''$.


### Spline2D <a name="Spline"></a> (_class_)



### Quartic/Quintic Polynomial

<blockquote><strong><em><font color="#ff0000"> To Be Accomplished</font></em></strong></blockquote>


## SensorUtils

Classes and functions of spatial information and its convertion with the corresponding data structures in various simulators.

- `Location`

- `Rotation`

- `Transform`

- `BoundingBox`

<blockquote><strong><em><font color="#ff0000"> To Be Accomplished</font></em></strong></blockquote>


## VehicleUtils

<blockquote><strong><em><font color="#ff0000"> To Be Accomplished</font></em></strong></blockquote>
