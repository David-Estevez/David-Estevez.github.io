---
folder: research
keywords: modular robots
permalink: research-modular-repy-2.0.html
sidebar: research
title: REPY-2.0
toc: false
---


<img class="img-rounded" src="img/research/repy-2.0/gallery/repy-2.0_05.jpg" alt="REPY-2.0 feature picture">

Open source module for Modular Robots.

![OpenSCAD render of the design](img/research/repy-2.0/first_prototype_scad.png)

## Introduction
The REPY-2.0 is an open source mechanical module for researching Modular Robotics. It is designed to be printed on a Low-cost 3D printer, like a [RepRap](http://reprap.org/wiki/Main_Page).

The main points taken into account when designed were:
  * **Symmetry**. This way, the robot can move whatever the orientation of the module is.
  * **Low-cost**. Modular robotics is usually a expensive area of research due to the fact that many small independent robots (modules) have to be built in order to build the main robot. Having a 3D printable design enables us to lower the cost of each module.
  * **Customization**. With the same code it can be able to generate different modules according to the electronics and motors chosen. If our motor or board is not yet implemented we can do it easily by using the existent modules as examples, and with our new module the program will be able to generate a custom REPY-2.0 module.

## Gallery
These are some examples of REPY-2.0 modules:
{{gallery>wiki:repy-2.0:gallery?200x200&4 }}

## User's manual
### Printing
For each module, one lower part and one upper part are needed.

STL files for printing can be found at:
  * [Thingiverse](http://www.thingiverse.com/thing:99207)
  * Latest version of the stl files can be found at the [git repository](https://github.com/David-Estevez/REPY-2.0/tree/master/stl)


**Note:** Not all of them have been printed and tested. At this moment only the following ones are validated:
  * **REPY-2.0 for Fake Futaba 3003s servo**: lower part and rounded, 4-arms and 6-arms horns.
  * **REPY-2.0 for Tower Pro SG90 servo**: lower part and 2-arms horn.
  * **REPY-2.0 for Futaba 3003s servo**: lower part and rounded horn.

### Assembly

#### Hardware requirements

For the assembly of the Futaba servo REPY module you need:
  * 1x Upper part of the module printed.
  * 1x Lower part of the module printed.
  * 1x Futaba 3003s Servo 
  * 4x M3x12 screws (minimum 2)
  * 4x M3 nuts (minimum 2)
  * 4x M3 washers (minimum 2)

If using other kind of servo the size of the screws may change, as well as its quantity, but the basic assembly process is very similar.

#### Visual assembly instructions
{{gallery>wiki:repy-2.0:assembly?200x200&4 }}

### Play with it!
Some examples of the REPY-2.0 in movement:

<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/gjrMeOpGr2s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/H3VW2Z-FlzI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/l1j4gek27yQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

## Developer's manual
The REPY-2.0 module has been created with the Object Oriented Mechanics Library ([OOML](https://github.com/avalero/OOML)), that allows us to create mechanical parts using the object-oriented programming paradigm. As we are working with (physical) objects, it makes a lot of sense to use object-oriented programming as we can manipulate the objects in a more intuitive way.

The REPY-2.0 module is not only parametric, but fully object-oriented, which means that you may pass as arguments to the constructor a servo and a PCB board objects and a suitable module for them will be generated. Those servo and PCB objects have to implement a certain data interface in order for the REPY-2.0 constructor to access their most characteristic parameters. In the following section those interfaces are specified and explained.

A explanation of the meaning of the main parameters of the objects that define a REPY-2.0 module is provided as plans in which those parameters appear as labels on the dimensions. Those plans may help to comprehend the source code of the module.

### Doxygen documentation
The best way to know how this works is to take a look at the [Doxygen documentation](http://david-estevez.github.io/REPY-2.0/).

### Code structure
To construct complex objects from other simpler ones some operations like the intersection, union, difference, etc can be used. But, most of the times, those operations are not enought to define the object. We usually need to know the main dimensions of the object in order to be able to place it in its position before carrying out the difference of both, for example.

To be able to do so, the object must have a public data interface that returns those main dimensions when needed. 

### OOML Objects
#### BasicServo
A BasicServo is a simplification of a servo, composed by a box with two legs and a cylinder. It implements a basic data interface that specifies the main dimensions of the servo.

Using inheritance, this BasicServo can be used to construct other more complex servos, while keeping the compatibility with the objects that use the BasicServo to be built, as the REPY-2.0.

This means that if we own a servo that is not supported by the OOML yet, we can build it ourselves, by inheriting all the main parameters of the BasicServo, and then, if we want to, creating a more accurate external shape. Then, we will be able to use it to create a REPY-2.0 module.

The following gallery shows the most important dimensions of a BasicServo.

{{gallery>wiki:repy-2.0:?ooml_basicservo*&200x200&4 }}

#### BasicSquaredPCB
A BasicSquaredPCB is, as its name suggests, a very basic implentation of a squared PCB with holes. One example of a real PCB with this shape would be the [SkymegaSMD](research-modular-skymegasmd.html).

As one of the requirements for the REPY-2.0 modules was symmetry, the best PCB to use with them is, in principle, also squared. In this moment only the SkyMega board is implemented, and without any detail, only with the main dimensions, but anyone could derive a more realistic model for it that would still be compatible with the module.

{{gallery>wiki:repy-2.0:?ooml_basicsquaredpcb*&200x200&4 }}

#### REPY module
A REPY module combines the information obtained by a BasicServo and a PCB and creates itself with the right dimensions.

{{gallery>wiki:repy-2.0:?ooml_repymodule*&200x200&4 }}

## Source code

Sources for this project can be found on [GitHub](https://github.com/David-Estevez/REPY-2.0).

## Acknowledgements

This module is based on the work of [Juan González Gómez (Obijuan)](http://www.iearobotics.com/wiki/index.php?title=Juan_Gonzalez:Main). For more info on modular robots visit: [Módulos REPY-1 (Spanish)](http://www.iearobotics.com/wiki/index.php?title=Módulos_REPY-1)

<!--{% include links.html %}-->