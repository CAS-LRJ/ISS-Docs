---
layout: default
title: Lanelet2 Global Planner
parent: Planning
nav_order: 2
---

## Lanelet2Planner<a name="Lanelet2Planner"></a>
A global trajectory planner based on Lanelet2 HD-Map. 
The implementation relies on the [Lanelet2 Python API](https://github.com/fzi-forschungszentrum-informatik/Lanelet2). 
Currently, the global planner will find the closest lanelets for both the start point and the end point. 
Then, it will use the Lanelet2 routing module to generate a submap containing all possible lanelets from the start lanelet to the end lanelet. 
A trajectory will then be generated using the modified flood-fill algorithm so that it will connect the start point to the end point: Start point -> Start lanelet -> End lanelet -> End point.

{: .note }
The ISS global planner module currently uses the Lanelet2 HDMap format. 
Since the Lanelet2 Python API only supports Linux systems, this module may not work properly in other platforms. 
We will separate the mapping and the planning module apart in a future release and support more HDMap formats (e.g. OpenDrive).

### Instance Variables
- **<font color="#f8805a">lanelet_map</font>** (_lanelet2.core.LaneletMap_)  
The lanelet2 HDMap for current location.
- **<font color="#f8805a">traffic_rules</font>** (_lanelet2.traffic\_rule_)  
The lanelet2 definition of traffic rules of current map.
- **<font color="#f8805a">collision_detector</font>** (_utils.vehicleutils.CollisionChecker_)  
The collision checker of solid road line.
- **<font color="#f8805a">reverse_y</font>** (_boolean_)  
When <b>True</b> the y-coordinate will be reversed. (Left-hand to Right-hand coordinates, vice versa)

<!-- ### Methods
- <a name="carla.Sensor.listen"></a>**<font color="#7fb800">listen</font>**(<font color="#00a6ed">**self**</font>, <font color="#00a6ed">**callback**</font>)<button class="SnipetButton" id="carla.Sensor.listen-snipet_button">snippet &rarr;</button>  
The function the sensor will be calling to every time a new measurement is received. This function needs for an argument containing an object type [carla.SensorData](#carla.SensorData) to work with.  
    - **Parameters:**
        - `callback` (_function_) - The called function with one argument containing the sensor data.  
- <a name="carla.Sensor.stop"></a>**<font color="#7fb800">stop</font>**(<font color="#00a6ed">**self**</font>)  
Commands the sensor to stop listening for data.   -->