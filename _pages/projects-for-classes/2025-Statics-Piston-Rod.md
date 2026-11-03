---
layout: project
title: Statics Piston-Rod Maximization
description: Statics class project 
technologies: [google sheets]
image: /assets/images/PistonMechanism.png
---


As part of a class project I was asked to design a system made up of a rod, 3 pin joints, and a piston to lift the maximum possible load. This system had to have a rod of length between 50 to 150 cm, 2 pin joints located on the ground, 1 pin joint at any point, and a linear actuator chosen from a catalog.


This is how I solved the problem:
- I solved the problem via parameters and tried different possible values to find the maximum output force
- I selected the IMA 55 RNO5 piston for its maximum force of 8,050 lb.
- I solved for F max in terms of parameters via moment equilibrium about A
- After testing different parameter values in google sheets I found final values of 
            L= 0.5 m
            x = 0.285
            This would produce a maximum Weight that could be lifted of 4588.5 lbs

This problem was then expanded to include Beam deflection and chosing an appropriate geometry. I found maximum deflection and chose a cross sectional geometry that would cause vertical deflection to be less than 2% of the beam's length. The maximum deflection was found to be 0.0094mm. The cross section geometry chosen to fulfill these requirements was a hollow steel beam with an width of 50 mm, height of 25 mm, and wall thickness of 3mm.
![Equations shown]({{ "/assets/images/DeflectionBeam.png" | relative_url }}){: .inline-image-r style="width: 300px"}            



