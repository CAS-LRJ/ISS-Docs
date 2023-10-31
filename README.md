# ISS

Intelligent Self-driving System (ISS) is a modular framework written in Python and C++ with the aim to build an extensible workspace tailored to research. This framework will contain both traditional and deep learning algorithms for self-driving related tasks such as perception, localization, mapping, prediction, planning, and control. The modular design with minimal dependency on external libraries can provide a transparent and clean workspace for researchers to evaluate algorithms for autonomous driving systems.

![ISS Architecture](assets/ISS_Framework.png)

## Simulator Demos
At present, the ISS framework has the capability to deploy and test algorithms using simulator data. Upon integrating sensor data from the CARLA simulator into our framework, we can evaluate a range of algorithms. Additionally, corresponding control algorithms can be employed to maneuver the simulated vehicles. Here are some demonstrations.

## Minicar Demos
In addition to simulation results, if the sensor data from the minicar is transmitted back to the ISS via ROS, the ISS can leverage the sensory data to accomplish a variety of tasks and exert control over the physical minicar.

<!-- ## Our Works

Currently, we have leveraged components of the ISS for various tasks, including scene construction, autonomous driving safety verification, and adversarial attacks on perception models.

<video width="640" height="360" controls>
  <source src="assets/LeftCutInSmall.mp4" type="video/mp4">
</video>
{: .center-image }
A simple left cut-in scenario built
{: .text-center} -->