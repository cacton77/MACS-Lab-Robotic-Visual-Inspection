# MACS Lab Robotic Visual Inspection
*** 

:::{note}
This site is actively being updated.
:::

### Core Research
***

::::{grid} 1 2 2 3
:gutter: 1 1 1 2

:::{grid-item-card} 👁️‍🗨️ Viewpoint Generation
:link: viewpoint_generation/intro
:link-type: doc

Produce minimum number of un-obstructed viewpoints for complete surface imaging of complex geometries from only part CAD or point cloud scan and camera intrinsic information.

+++
[Learn more »](viewpoint_generation/intro)
:::

:::{grid-item-card} 📈 Traversal Optimization
:link: traversal_optimization/intro
:link-type: doc

Minimize inspection time through optimal ordering of viewpoints.

+++
[Learn more »](traversal_optimization/intro)
:::

:::{grid-item-card} 🔬 Manipulator Autofocus
:link: manipulator_focus/intro
:link-type: doc

Estimate and optimize image focus and quality, and maintain constant magnification through real-time adaptive visual servoing-based autofocus.

+++
[Learn more »](manipulator_focus/intro)
:::

:::{grid-item-card} 🧭 Point Cloud Registration
:link: point_cloud_registration/intro
:link-type: doc

Facilitate fixtureless inspection and part adaptability through single-shot depth information part library lookup and pose estimation.

+++
[Learn more »](point_cloud_registration/intro)
:::

:::{grid-item-card} 🔦 Illuminance Control
:link: illuminance_control/intro
:link-type: doc

Improve deployment environment adaptability and anomaly detection accuracy through source to surface lighting modeling and control.

+++
[Learn more »](illuminance_control/intro)
:::

:::{grid-item-card} 🔍 Anomaly Detection
:link: anomaly_detection/intro
:link-type: doc

Provide non-intrusive, minimally supervised AI model training data collection pipeline and adaptive models for detection of non-conforming image regions.

+++
[Learn more »](anomaly_detection/intro)
:::
::::

### Development Tools
***

::::{grid} 1 2 2 3
:gutter: 1 1 1 2

:::{grid-item-card} ⚙️ ROS 2
:link: development_tools/ros2
:link-type: doc

Flexible, modular robotics middleware framework for building distributed robotic systems.

+++
[Learn more »](development_tools/ros2)
:::

:::{grid-item-card} 🐧 Ubuntu
:link: development_tools/ubuntu
:link-type: doc

+++
[Learn more »](development_tools/ubuntu)
:::

:::{grid-item-card} 🐋 Docker
:link: development_tools/docker
:link-type: doc

+++
[Learn more »](development_tools/docker)
:::

::::

### Tutorials
***

::::{grid} 1 2 2 3
:gutter: 1 1 1 2

:::{grid-item-card} ROS2 Development in WSL2
:link: tutorials/wsl2_ros2_install
:link-type: doc

+++
[Learn more »](tutorials/wsl2_ros2_install)
:::

:::{grid-item-card} ROS2 Humble Tutorials
:link: tutorials/ros2_humble_tutorials
:link-type: doc

+++
[Learn more »](tutorials/ros2_humble_tutorials)
:::

:::{grid-item-card} Docker for ROS2 Development
:link: tutorials/ros2_docker
:link-type: doc

+++
[Learn more »](tutorials/ros2_docker)
:::

::::


```{toctree}
:hidden:

overview.md
```

```{toctree}
:hidden: 
:caption: 👁️‍🗨️ Viewpoint Generation

viewpoint_generation/intro.md
```

```{toctree}
:hidden: 
:caption: 📈 Viewpoint Traversal Optimization

traversal_optimization/intro.md
```

```{toctree}
:hidden: 
:caption: 🔬 Manipulator Focus

manipulator_focus/intro.md
manipulator_focus/autofocus.md
manipulator_focus/focus_metrics.md
manipulator_focus/control_algorithm.md
```

```{toctree}
:hidden: 
:caption: 📸 gPhoto2 ROS2

gphoto2_ros2/intro.md
```

```{toctree}
:hidden: 
:caption: 📃 Papers

papers/viewpoint_generation_paper.md
papers/focus_metrics_paper.md
```

```{toctree}
:hidden:
:caption: Tools and Tutorials
development_tools/development_tools.md
tutorials/tutorials.md
```

```{toctree}
:hidden:
:caption: Contributions

contact.md
```

[commonmark]: https://commonmark.org/
[github-ci]: https://github.com/executablebooks/MyST-Parser/workflows/continuous-integration/badge.svg?branch=master
[github-link]: https://github.com/executablebooks/MyST-Parser
[codecov-badge]: https://codecov.io/gh/executablebooks/MyST-Parser/branch/master/graph/badge.svg
[codecov-link]: https://codecov.io/gh/executablebooks/MyST-Parser
[rtd-badge]: https://readthedocs.org/projects/myst-parser/badge/?version=latest
[rtd-link]: https://myst-parser.readthedocs.io/en/latest/?badge=latest
[black-badge]: https://img.shields.io/badge/code%20style-black-000000.svg
[pypi-badge]: https://img.shields.io/pypi/v/myst-parser.svg
[pypi-link]: https://pypi.org/project/myst-parser
[conda-badge]: https://anaconda.org/conda-forge/myst-parser/badges/version.svg
[conda-link]: https://anaconda.org/conda-forge/myst-parser
[black-link]: https://github.com/ambv/black
[github-badge]: https://img.shields.io/github/stars/executablebooks/myst-parser?label=github
[markdown-it-py]: https://markdown-it-py.readthedocs.io/
[markdown-it]: https://markdown-it.github.io/
[rst-to-myst]: https://rst-to-myst.readthedocs.io