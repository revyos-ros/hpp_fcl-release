HPP-FCL — An extension of the Flexible Collision Library
=======

<p align="center">
  <a href="https://gepgitlab.laas.fr/humanoid-path-planner/hpp-fcl/commits/master/"><img src="https://gepgitlab.laas.fr/humanoid-path-planner/hpp-fcl/badges/master/pipeline.svg" alt="Pipeline status"/></a>
  <a href="https://gepettoweb.laas.fr/hpp/hpp-fcl/doxygen-html/index.html"><img src="https://img.shields.io/badge/docs-online-brightgreen" alt="Documentation"/></a>
  <a href="http://projects.laas.fr/gepetto/doc/humanoid-path-planner/hpp-fcl/master/coverage/"><img src="https://gepgitlab.laas.fr/humanoid-path-planner/hpp-fcl/badges/master/coverage.svg?job=doc-coverage" alt="Coverage report"/></a>
  <a href="https://anaconda.org/conda-forge/hpp-fcl"><img src="https://img.shields.io/conda/dn/conda-forge/hpp-fcl.svg" alt="Conda Downloads"/></a>
  <a href="https://anaconda.org/conda-forge/hpp-fcl"><img src="https://img.shields.io/conda/vn/conda-forge/hpp-fcl.svg" alt="Conda Version"/></a>
  <a href="https://badge.fury.io/py/hpp-fcl"><img src="https://badge.fury.io/py/hpp-fcl.svg" alt="PyPI version"></a>
</p>

[FCL](https://github.com/flexible-collision-library/fcl) was forked in 2015. Since then, a large part of the code has been rewritten or removed (for the unused and untested part).
The broadphase was reintroduced by J. Carpentier in 2022 based on the FCL version 0.7.0.

## New features

Compared to the original [FCL](https://github.com/flexible-collision-library/fcl) library, the main new features are:
- a dedicated and efficient implementation of the GJK algorithm (we do not rely anymore on [libccd](https://github.com/danfis/libccd))
- the support of safety margins for collision detection
- an accelerated version of Collision Detection *à la Nesterov* which leads to increased performances (up to a factor 2). More details are available in this [paper](https://hal.archives-ouvertes.fr/hal-03662157/)
- the computation of a lower bound of the distance between two objects when collision checking is performed and no collision is found
- the implementation of Python bindings for easy code prototyping
- the support of height fields, capsule shapes, etc.
- the fix of various bugs

This project is now used in many robotics frameworks such as [Pinocchio](https://github.com/stack-of-tasks/pinocchio), an open-source software which implements efficient and versatile rigid body dynamics algorithms and the [Humanoid Path Planner](https://humanoid-path-planner.github.io/hpp-doc), an open-source software for Motion and Manipulation Planning.

## Performances

Unlike the original FCL library, HPP-FCL implements the well-established GJK algorithm and [its variants](https://hal.archives-ouvertes.fr/hal-03662157/) for collision detection and distance computation. These implementations lead to state-of-the-art performances, as depicted by the figure below. In particular, you can observe that GJK-based approaches largely outperform solutions based on classic optimization solvers (e.g., QP solver like [ProxQP](https://github.com/Simple-Robotics/proxsuite)), notably for large geometries composed of tens or hundred of vertices.

<p align="center">
  <img src="./doc/images/hpp-fcl-performances.jpg" width="600" alt="HPP-FCL performances" align="center"/>
</p>

## Acknowledgments

The development of **HPP-FCL** is actively supported by the [Gepetto team](http://projects.laas.fr/gepetto/) [@LAAS-CNRS](http://www.laas.fr), the [Willow team](https://www.di.ens.fr/willow/) [@INRIA](http://www.inria.fr) and, to some extend, [Eureka Robotics](https://eurekarobotics.com/).

