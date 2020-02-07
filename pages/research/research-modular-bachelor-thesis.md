---
folder: research
keywords: modular robots
permalink: research-modular-bachelor-thesis.html
sidebar: research
title: Bachelor's Thesis
toc: false
---


<img class="img-rounded" src="img/research/bach_thesis/gallery/conf-11-2-3.png" alt="Bachelor's Thesis feature picture">

The objective of my Bachelor's Thesis, titled " Locomotion Gaits Through Hormone-based Controller in Modular Robots", was to develop a modular robot able to learn locomotion gaits for different configurations, and then to select the most appropiate gait according to the current configuration of the robot. This system is distributed, so that each module has its own controller (the same for all modules), and all of them communicate and collaborate in order to detect the current modular robot configuration and select the correct gait.

<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/a9mfkdL66Tc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></p>

## Abstract

Modular robots are robots composed of multiple units, called 'modules'. Each module is an independent robot, with its own control electronics, actuators, sensors, communications and power. These modules can change their position and configuration in order to adapt to the requirements of the situation, making modular robot suitable for tasks that involve unknown or unstructured terrains, in which a robot cannot be designed specifically for them. Some examples of those applications are space exploration, battlefield reconnaissance, finding victims among the debris in natural catastrophes and other similar tasks involving complicated terrains, which require a high versability.

But this versability comes with several drawbacks. As modular robots are composed of several independent robots, the nature of their controller is distributed, which difficults their design and programming, requiring additionally a robust communication protocol to share information among modules. The high number of modules also results in a robot with a with number of degrees of freedom, for which achieving the coordination required for locomotion becomes increasingly difficult. Finally, as the modules are fully independent robots, the cost of researching modular robotics is usually very high, since the price of building a single robot has to be multiplied by the high number of modules.

This thesis addresses those three mentioned problems: obtaining optimal locomotion gaits from a biologically inspired approach, using sinusoidal oscillators whose parameters are found through evolutionary optimization algorithms; developing a homogenous, distributed controller based on digital hormones that can recognize the current robot configuration and select the proper gait; and the development of a low-cost modular robotic platform to reseach locomotion gaits for different configurations.

## Software: Hormodular
The software implemented for this thesis was designed to be modular enough so that multiple types of modular robot and modules could be used for evolution and evaluation of gaits. 

The main class diagram is the following:

![main class diagram picture](img/research/bach_thesis/class_diagram_main.png)

Chapter 3 of the thesis deals with the software design as well as the meaning and explanation of the details of the different classes used.

All the software can be found in the github repository [Hormodular](https://github.com/David-Estevez/hormodular), and the instructions for compiling and running this software are included at the end of the aforementioned chapter.

## Hardware
The hardware used to build the different modular robots was based on the work of Juan Gonzalez-Gomez (Obijuan), specifically the Skymega board for controlling the hobby servos and the REPY-1 modules to compose the modular robot body.

## Electronics
The [SkymegaSMD](research-modular-skymegasmd.html) board is a improved version of the [SkyMega board](http://www.iearobotics.com/wiki/index.php?title=SkyMega), designed by [Juan Gonzalez-Gomez](https://twitter.com/Obijuan_cube).

![skymegasmd board picture](img/research/bach_thesis/hardware_skymegasmd.jpg)

The [SkymegaSMD](research-modular-skymegasmd.html) board introduces the following improvements:

* The board is populated with surface-mount compoments (SMD) instead of through-hole components (THD). Using SMD components reduces the amount of PCB surface required by each component. This has allowed us to design a cleaner component layout, add extra components and route the board on the top layer, leaving the bottom layer entirely as a ground plane, reducing electrical noise and interferences.	
* A linear, Low-Dropout (LDO) regulator was added to the circuit in order to have a stable 5V supply to the microcontroller. A stable supply is required, for example, if using the analog inputs to measure a voltage. In this case, if the supply is not constant, the measured values will not have a common reference and will vary even if the voltage measured is the same.	
* The supply for the hobby servos has been split into two different power connectors. One of them supplies the LDO regulator that powers the microcontroller and 4 of the 8 servos that the board allows to use, whereas the other connector supplies the remaining 4 servos. The reason the supply has been split is because the hobby servos consume a high amount of current, and the inductive component generated by the DC motor introduces a large amount of noise in the power lines, that even resets the microcontroller when the 8 servos are connected to a single supply in the original Skymega board. To reduce the effect of the motors on the power supply of the microcontroller,  a capacitor was added next to each servo connector, and the power for the servos is supplied directly from the connector, not passing through the LDO regulator, so the regulated line is as clean as possible.
* The expansion port has been split into several smaller headers, to reduce the space occupied by the connector. A extra header has been added on the botton of the board for the connection with a optional Bluetooth serial transceiver.
* Two LEDs for power indication on both supplies and two LEDs for serial port transmission signalling were added.

The boards were designed with KiCad and sent to be manufactured in SeeedStudio, a chinese manufacturer for very small batches of PCB prototypes. When they arrived, they were assembled by hand, and tested. 

## Module: REPY-2.1

This module, based on the [REPY-1 module](http://www.iearobotics.com/wiki/index.php?title=M%C3%B3dulos_REPY-1), improves the original capabilities of the REPY-1 module, and adds the posibility of forming 2D modular robots, with the new connectors on both modular sides.

{{ :wiki:othersdef:bach_thesis:hardware_repy_2_1_real.jpg?400 |}}

Apart from the side holes, the REPY-2.1 module is very similar to the REPY-2.0 module, and information for both versions of the module can be found here:
  * [REPY-2.1](research-modular-repy-2.1.html)
  * [REPY-2.0](research-modular-repy-2.0.html)

## Gallery
{{gallery>:wiki:othersdef:bach_thesis:gallery?200x200&3}}

##  Download Thesis (and sources)
  * The thesis and the LaTeX sources to compile it are available in the [Hormodular repository](https://github.com/David-Estevez/hormodular).
  * Direct link for the thesis PDF [here](https://github.com/David-Estevez/hormodular/raw/master/thesis/Bachelor_thesis_final_def.pdf).
  * Direct link for the thesis defense slides [here](https://github.com/David-Estevez/hormodular/raw/master/thesis/Bachelors_Thesis_presentation.pdf).

## Acknowledgements

* Idea and technical support: [Juan González Gómez (Obijuan)](http://www.iearobotics.com/wiki/index.php?title=Juan_Gonzalez:Main)
* Thesis advisor: Avinash Ranganath

<!--{% include links.html %}-->