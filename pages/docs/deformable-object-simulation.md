---
title: Deformable Object Simulation
keywords: deformable objects, simulation, software
sidebar: home_sidebar
permalink: deformable-object-simulation.html
folder: docs
summary: A collection of helpful resources for Deformable Object Simulation
---

# Blender-based
* [On what Cloth Simulation Model is Blender Cloth Physics Based?](https://blender.stackexchange.com/questions/8247/on-what-cloth-simulation-model-is-blender-cloth-physics-based)
* [Armory3D - Build Games in Blender](https://armory3d.org/)
* [UPBGE - Fork from old Blender Game Engine](https://upbge.org/)

## Interactive cloth simulation
This is as close as one can get to an interactive simulation with Blender.

1. Create a subdivided plane and assign it a cloth modifier to create the cloth.
2. Create some kind of surface with collisions enabled to hold the garment. (optional)
3. Create a vertex group with the vertex that will be pinned (the vertex from which the cloth will hang).
4. Set that vertex group as pinning vertex group in cloth modifier.
5. With the vextex selected, use ctrl+h to add a hook to a new object (an empty object).
6. With simulation enabled (animation being played), moving the empty results in moving the garment. Note that the hook modifier should be applied before the cloth modifier.

Source: [jan van den Hemel - Twitter](https://twitter.com/JanvandenHemel/status/1163154199170945030)

# Position-based Dynamics Simulators

* [Position Based Elastic Rod for Jan Bender's PBD library [GitHub]](https://github.com/korzen/PositionBasedDynamics-ElasticRod)
* [InteractiveComputerGraphics/PositionBasedDynamics [GitHub]](https://github.com/InteractiveComputerGraphics/PositionBasedDynamics) 
