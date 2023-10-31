---
title: Install
layout: home
nav_order: 1
---
# ISS

Intelligent Self-driving System (ISS) is a modular framework written in Python and C++ with the aim to build an extensible workspace tailored to research. This framework will contain both traditional and deep learning algorithms for self-driving related tasks such as perception, localization, mapping, prediction, planning, and control. The modular design with minimal dependency on external libraries can provide a transparent and clean workspace for researchers to evaluate algorithms for autonomous driving systems.

The code of ISS can be downloaded from its [*Github Repository*](https://github.com/CAS-LRJ/ISS).

## Dependencies

ISS is dependent on a minimal set of Python libraries; another set of recommended libraries can be optionally installed to improve its functionalities.
Also, some examples will be written in Jupyter Notebook.

### Minimal Dependencies

Python libraries required by ISS.

```yaml
carla=0.9.13
cython=0.29.36
lanelet2=1.2.1 (manylinux)
networkx=3.1
numpy=1.24.3
open3d=0.17.0
opencv-python=4.8.0.76
pytorch=1.13.1
scikit-learn=1.3.0
pyyaml=6.0.1
spconv-cu118=2.3.6
open3d=0.17.0
```

### Optional Libraries

Optional packages that can be installed to improve ISS.

```yaml
matplotlib=3.5.3
pandas=2.0.3
dubins=1.0.1
commonroad-io=2022.3
commonroad-route-planner=2022.3
commonroad-scenario-designer=0.6.1
commonroad-vehicle-models=3.0.2
```

## Build

After cloning the [ISS repository](https://github.com/CAS-LRJ/ISS), run the following command to build the ISS framework:

```bash
python setup.py build_ext --inplace
```

We suggest using a virtual environment to avoid conflicts between the Python libraries installed for ISS and one installed system-wide, in particular in Windows systems. Virtual environments can be managed by using e.g. [Anaconda](https://www.anaconda.com/) or [Miniconda](https://docs.conda.io/projects/miniconda/en/latest/). Cython 3.0 is currently not supported, so please use Cython version 0.29 instead. Cython versions 0.29.33 and 0.29.36 have been tested. For simulators' version control, we are currently using **CARLA 0.9.13** and **BeamNG 0.27.2.0**, therefore you should use **carla==0.9.13** and **beamngpy==1.25.1** in your virtual enviroment.

**Caution**: If you are using a Windows system, Microsoft Visual C++ 14.0 or later is required. To compile this project locally, you should have *visual-cpp-build-tools* pre-installed.

## Run tasks

### CARLA Data Collector

Run the following command to collect various kinds of sensor data from CARLA:

```bash
python run_carla.py
```

Make sure the CARLA 0.9.13 Server is running before starting `run_carla.py`. Data will be saved in `resources/data/carla`, which can be changed by modifying the environment variables `{RAW_DATA, DATASET}_PATH`.

## Current Release

## Release v1.0.1alpha (Oct 11)

Major updates:

- Add 3d detection & torch script wrapper
- Add GNSS sensor data type
- Add link of collected CARLA object detection dataset
- Prepare for implementing EM Planner
