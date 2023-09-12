---
layout: default
title: Lanelet2 Global Planner
parent: Planning
nav_order: 2
---

## Lanelet2Planner<a name="Lanelet2Planner"></a>
A global trajectory planner based on Lanelet2 HD-Map. The implementation relies on [Lanelet2 Python API](https://github.com/fzi-forschungszentrum-informatik/Lanelet2). Currently, the global planner will find closest lanelets for both start point and end point. Then, it will utilise the Lanelet2 routing module to generate the submap contains all possible lanelets from the start lanelet to the end lanelet. A trajectory will be generated using the modified flood-fill algorithm. The final trajectory will connect the start point to the end point. (Start Point -> Start Lanelet -> End Lanelet -> End Point)

{: .note }
The global planner module currently uses Lanelet2 HDMap format. Since the Lanelet2 Python API only support linux system, this module may not work properly in other platforms. We will seperate the mapping and the planning module apart in further release and support more HDMap format (e.g. OpenDrive).

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