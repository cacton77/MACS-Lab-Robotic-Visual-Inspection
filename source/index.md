# MACS Lab Robotic Visual Inspection
*** 

:::{note}
This site is actively being updated.
:::

::::{grid} 1 2 2 3
:gutter: 1 1 1 2

:::{grid-item-card} 👁️‍🗨️ Viewpoint Generation
:link: viewpoint_generation/intro.md
<!-- :link-type: ref -->

MyST extends the CommonMark syntax specification, to support technical authoring features such as tables and footnotes.

+++
[Learn more »](viewpoint_generation/intro.md)
:::

:::{grid-item-card} 📈 Traversal Optimization
:link: traversal_optimization/intro.md
<!-- :link-type: ref -->

Use the MyST role and directive syntax to harness the full capability of Sphinx, such as admonitions and figures, and all existing Sphinx extensions.

+++
[Learn more »](traversal_optimization/intro.md)
:::

:::{grid-item-card} 🦾 Manipulator Focus
:link: manipulator_focus/intro.md
<!-- :link-type: doc -->

MyST-parser can be configured at both the global and individual document level,
to modify parsing behaviour and access extended syntax features.

+++
[Learn more »](manipulator_focus/intro.md)
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
:caption: 🦾 Manipulator Focus

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