---
layout: default
title: CARLA Sensors
parent: Sensors
nav_order: 1
---

# Sensors in CARLA<a name="Sensor"></a>

Sensors in CARLA compound a specific family of actors that are quite diverse and unique from the other CARLA actors; they model different sensing capabilities that can be used in self-driving systems. 
Sensors are represented by CARLA actors that are normally spawned as attachment/sons of a vehicle. 
Sensors are thoroughly designed to retrieve different types of data that they are listening to. 

Most sensors can be divided in two groups: those receiving data on every tick (cameras, point clouds and some other specific sensors) and those who only receive under certain circumstances (trigger detectors). CARLA provides a specific set of sensors and their blueprint can be found in [carla.BlueprintLibrary](#carla.BlueprintLibrary). 

### Instance Variables
- <a name="carla.Sensor.is_listening"></a>**<font color="#f8805a">is_listening</font>** (_boolean_)  
When <b>True</b> the sensor will be waiting for data.  

### Methods
- <a name="carla.Sensor.listen"></a>**<font color="#7fb800">listen</font>**(<font color="#00a6ed">**self**</font>, <font color="#00a6ed">**callback**</font>)<button class="SnipetButton" id="carla.Sensor.listen-snipet_button">snippet &rarr;</button>  
The function the sensor will be calling to every time a new measurement is received. This function needs for an argument containing an object type [carla.SensorData](#carla.SensorData) to work with.  
    - **Parameters:**
        - `callback` (_function_) - The called function with one argument containing the sensor data.  
- <a name="carla.Sensor.stop"></a>**<font color="#7fb800">stop</font>**(<font color="#00a6ed">**self**</font>)  
Commands the sensor to stop listening for data.  

## CarlaCamera

The "RGB" camera acts as a regular [camera](index.html#Camera) capturing images from the scene.
A CARLA camera can be tuned with respect to multiple parameters, such as `sensor_tick` and `enable_postprocess_effects`. 
The numeric `sensor_tick` parameter controls how fast we want the sensor to capture the scene: 
for example, a value of 1.5 means that we want the sensor to capture an image each second and a half. The value 0.0 is used as default and it instructs the camera to capture images as fast as possible.

The `enable_postprocess_effects` parameters allows the user to increase the realism of the captured images, by applying the corresponding set of post-process effects:

* __Vignette:__ darkens the border of the screen.
* __Grain jitter:__ adds some noise to the render.
* __Bloom:__ intense lights burn the area around them.
* __Auto exposure:__ modifies the image gamma to simulate the eye adaptation to darker or brighter areas.
* __Lens flares:__ simulates the reflection of bright objects on the lens.
* __Depth of field:__ blurs objects near or very far away from the camera.


## CarlaLiDAR

This sensor simulates a rotating [LiDAR](index.html#LiDAR) implemented using ray-casting.
The points are computed by adding a laser beam for each channel distributed in the vertical FOV. 
The rotation is simulated by computing the horizontal angle corresponding to how much the LiDAR rotated between two consecutive frames taken with frequency `FPS`, that is, the LiDAR rotation angle in `1/FPS` seconds. 
The point cloud is calculated by doing a ray-cast for each laser beam in every step.
`points_per_channel_each_step = points_per_second / (FPS * channels)`

A LIDAR measurement contains a package with all the points generated during an interval of length `1/FPS`. 
During this interval the physics of the world are not updated so all points in the measurement reflect the same "static picture" of the scene.

This output contains a cloud of simulation points and thus, it can be iterated to retrieve a list of their [`carla.Location`](python_api.md#carla.Location):

```py
for location in lidar_measurement:
    print(location)
```

The information of the LiDAR measurement is encoded by means of 4D points. 
The first three dimensions represent the space points in the usual XYZ spatial coordinates; 
the last one stands for the intensity loss during the travel. 
This intensity is computed by the following formula.
<br>


`a` — Attenuation coefficient. This may depend on the sensor's wavelenght, and the conditions of the atmosphere. It can be modified with the LiDAR attribute `atmosphere_attenuation_rate`.
`d` — Distance from the hit point to the sensor.

For a better realism, points in the cloud can be dropped off. This is an easy way to simulate loss due to external perturbations. This can done combining two different parameters.

*   __General drop-off__ — Proportion of points that are dropped off randomly. This is done before the tracing, meaning the points being dropped are not calculated, thus improving the performance. If `dropoff_general_rate = 0.5`, half of the points will be dropped.
*   __Instensity-based drop-off__ — For each point detected, and extra drop-off is performed with a probability based in the computed intensity. This probability is determined by two parameters: `dropoff_zero_intensity` and `dropoff_intensity_limit`, where is the probability of points with zero intensity to be dropped while `dropoff_intensity_limit` is a threshold intensity above which no points will be dropped. The probability of a point within the range to be dropped is a linear proportion based on these two parameters.

Additionally, the `noise_stddev` attribute makes for a noise model to simulate unexpected deviations that appear in real-life sensors. For positive values, each point is randomly perturbed along the vector of the laser beam. The result is a LiDAR sensor with perfect angular positioning, but noisy distance measurement.

The rotation of the LiDAR can be tuned to cover a specific angle on every simulation step (using a [fixed time-step](adv_synchrony_timestep.md)). For example, to rotate once per step (full circle output, as in the picture below), the rotation frequency and the simulated FPS should be the same; 
this can be obtained by <br>__1.__ Setting the sensor's rotation_frequency attribute `sensors_bp['lidar'][0].set_attribute('rotation_frequency','10')`. <br> __2.__ Running the simulation using the option `--fps=N`, e.g., `python3 config.py --fps=10`.

## CarlaGNSS

* __Blueprint:__ sensor.other.gnss
* __Output:__ [carla.GNSSMeasurement](python_api.md#carla.GnssMeasurement) per step (unless `sensor_tick` says otherwise).

This sensors models a [GPS receiver](index.html#GPS_IMU) and it provides the current [GNSS position](https://www.gsa.europa.eu/european-gnss/what-gnss) of the vehicle the sensor is attached to. 
The current coordinates are calculated by adding the metric position to an initial geo reference location defined within the OpenDRIVE map definition.

#### GNSS attributes


| Blueprint attribute      | Type   | Default            | Description        |
| ------------------- | ------------------- | ------------------- | ------------------- |
| `noise_alt_bias`   | float  | 0\.0   | Mean parameter in the noise model for altitude.    |
| `noise_alt_stddev` | float  | 0\.0   | Standard deviation parameter in the noise model for altitude.  |
| `noise_lat_bias`   | float  | 0\.0   | Mean parameter in the noise model for latitude.    |
| `noise_lat_stddev` | float  | 0\.0   | Standard deviation parameter in the noise model for latitude.  |
| `noise_lon_bias`   | float  | 0\.0   | Mean parameter in the noise model for longitude.   |
| `noise_lon_stddev` | float  | 0\.0   | Standard deviation parameter in the noise model for longitude. |
| `noise_seed`       | int    | 0      | Initializer for a pseudorandom number generator.   |
| `sensor_tick`      | float  | 0\.0   | Simulation seconds between sensor captures (ticks).            |

<br>

#### Output attributes


| Sensor data attribute            | Type  | Description        |
| ----------------------- | ----------------------- | ----------------------- |
| `frame`            | int   | Frame number when the measurement took place.      |
| `timestamp`        | double | Simulation time of the measurement in seconds since the beginning of the episode.        |
| `transform`        | [carla.Transform](<../python_api#carlatransform>)  | Location and rotation in world coordinates of the sensor at the time of the measurement. |
| `latitude`         | double | Latitude of the actor.           |
| `longitude`        | double | Longitude of the actor.          |
| `altitude`         | double | Altitude of the actor.           |