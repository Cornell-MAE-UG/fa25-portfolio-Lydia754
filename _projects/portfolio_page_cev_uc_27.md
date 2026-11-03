---
layout: project
title: Steering Linkages, Steering Wheel Supports, Steering Flat Plate
description: Cornell Electric Vehicles 2026 Projects (steering lead)
image: /assets/steering_architecture_overview.png
technologies: Autodesk Inventor, Ansys
---

## Overview

This year I am steering lead for the mechanical subteam of Cornell Electric Vehicles, I have 3 main projects alongside managing interfacing and design for the steering sub-projects. These projects are all for my steering subsystem of mechanical design for Cornell Electric Vehicles, which competes in the Shell Eco-marathon. 

### Core Projects:
1. **Steering Linkages:** Including Ackermann calculations and Finite Element Analysis (FEA).
2. **Steering Flat Plate:** Designed to allow more precise mounting connections and pocketed based on mounting holes for each project. Repeated Ansys modeling was performed to check deflection under main loading conditions (bump, brake, turn) to ensure pocketing results in minimal deflection.
3. **Steering Wheel Supports:** Redesigned following a baseplate redesign that removed wheel wells for simpler manufacturing. This change removed previous connection points for the steering wheel structure and decreased resistance to bending. The new design features a truss structure positioned above the pedals, reducing the moment arm associated with the supports compared to the previous design.

---

## Steering Subsystem Geometry & Architecture

### System Architecture Overview
<img src="{{ '/assets/steering_architecture_overview.png' | relative_url }}" alt="Overall Steering Architecture" style="display: block; margin: 1rem auto; width: 650px; max-width: 100%;" />

---

## Steering Linkages
<img src="{{ '/assets/steering_linkages_top_view.png' | relative_url }}" alt="Steering Linkage Assembly" style="display: block; margin: 1rem auto; width: 650px; max-width: 100%;" />

### Goals and Rule Requirements
- Achieve close to pure Ackermann geometry.
- Optimize Ackermann for a 10 m turning radius.
- Achieve 4.5 m turning radius minimum capability.
- Prevent interfacing issues with brake and accelerator pedals.
- Implement a steering plate for easier, precise hole spacing and assembly.
- Two-hand operation.
- Steering radius &lt; 6 m.
- Minimal mechanical play.

### Design Parameters
* **Tie Rod Length:** 13.27 in
* **Target Ackermann Percentage:** 104%

---

## Mathematical Analysis & Calculations

### Ackermann Calculations

#### Pure Inner Wheel Turning Radius
R<sub>i</sub> = &radic;[ (R - w/2)<sup>2</sup> + L<sup>2</sup> ]

R<sub>i</sub> = &radic;[ (6 - 0.44/2)<sup>2</sup> + 1.502<sup>2</sup> ] = **9.7815 m**

#### Pure Outer Wheel Turning Radius
R<sub>o</sub> = &radic;[ (R + w/2)<sup>2</sup> + L<sup>2</sup> ]

R<sub>o</sub> = &radic;[ (10 + 0.44/2)<sup>2</sup> + 1.502<sup>2</sup> ] = **10.0431 m**

#### Theoretical Steering Angles
* **Inner Steering Angle (&delta;<sub>i</sub>):**
  &delta;<sub>i</sub> = arcsin( L / R<sub>i</sub> ) = arcsin( 1.502 / 9.7815 )

* **Outer Steering Angle (&delta;<sub>o</sub>):**
  &delta;<sub>o</sub> = arcsin( L / R<sub>o</sub> ) = arcsin( 1.502 / 10.0431 ) = **8.269&deg;**

#### Ackermann Percentage Evaluation
$$\text{Ackermann } \% = \frac{(\delta_i - \delta_o)_{\text{actual}}}{(\delta_i - \delta_o)_{\text{ideal}}} \times 100$$

From CAD Sketch:
* &delta;<sub>i</sub> = 9.00&deg;
* &delta;<sub>o</sub> = 8.39&deg;

$$\text{Ackermann } \% = \frac{9.00 - 8.39}{8.833 - 8.269} \times 100 = 109.929\% \approx 110\%$$

*Note: Ackermann Steering is calibrated at 110% @ 10 m. Actual target calculation is revised to 104% due to the suspension-tierod interface being moved closer to the rack and pinion to resolve packaging issues.*

---

### Pinion Travel (4.5 m Turn Radius Requirement)

tan(&delta;) = L / R

For L = 1.50 m and R = 4.5 m:
* &delta; = 18.46&deg;
* &theta;<sub>r</sub> = 28.46&deg; + 18.46&deg; = 46.88&deg;

y = r &middot; sin(46.8&deg;) - sin(28.4&deg;)  
**&Delta;y = 72.4 mm = 2.85 in (per side)**

* **Total Required Rack Travel:** &ge; 5.7 in

---

## Structural Analysis & Simulation (FEA)

### Tie Rod FEA
<img src="{{ '/assets/tie_rod_fea_analysis.png' | relative_url }}" alt="Tie Rod Finite Element Analysis" style="display: block; margin: 1rem auto; width: 650px; max-width: 100%;" />

* **Load Condition:** 70.62 lbf applied axially from rack and pinion.
* **Material:** Aluminum 6061
* **Factor of Safety (FOS):** 15
* **Max Deformation:** 0.00298 mm

---

## Steering Wheel Supports
<img src="{{ '/assets/steering_wheel_support_cad.png' | relative_url }}" alt="Steering Wheel Support Structure" style="display: block; margin: 1rem auto; width: 650px; max-width: 100%;" />

### Design Strategy & Revisions
This design replaces previous iterations that anchored to a carbon fiber tube spanning between the wheel wells (removed following the baseplate redesign). 

An initial design attempted to anchor the supports to the aerodynamic side shell; however, hand calculations revealed excessive forces for non-load-bearing aero panels. The final iteration builds down directly to the carbon fiber baseplate, which is thicker and engineered for structural loads. The steering wheel shaft interfaces with the rack and pinion via a U-joint.

### Analysis & Hand Calculations
* **Steering Torque:** 12 N&middot;m
* **Max Moment at Support:** 14 N&middot;m

---

## Steering Flat Plate Analysis
<img src="{{ '/assets/steering_flat_plate_fea.png' | relative_url }}" alt="Steering Flat Plate Deflection FEA" style="display: block; margin: 1rem auto; width: 650px; max-width: 100%;" />

### Design & Function
The primary objective of the steering flat plate is to establish exact hole placements across multiple subsystem components. Direct drilling into the carbon baseplate introduces positioning errors, which historically caused assembly inefficiencies.

* **Plate Thickness:** 0.25 in
* **Hardware:** Pressed with 1/4-28 flush nuts
* **Offset:** Elevated 0.25 in off the baseplate via side and center standoffs.
* **Factor of Safety (FOS):** 15
* **Max Total Deformation (FEA):** 0.11236 mm

---

## Bill of Materials (BOM)

| Part | Link / SKU | Packages Needed | Price / Pkg | Vendor | Status |
| :--- | :--- | :---: | :---: | :--- | :--- |
| **Ball Joint Ends** | [McMaster 60645K32](https://www.mcmaster.com/60645K32) | 2 | \$4.71 | McMaster | FINAL |
| **Tie Rod Stock** | [McMaster 8974K28](https://www.mcmaster.com/8974K28) | 1 | \$7.56 | McMaster | FINAL |
| **45 Degree Supports** | McMaster 47065T188 | 2 | \$53.67 | McMaster | FINAL |
| **Wide CF Tubes** | McMaster 2040N16 | 1 | \$213.59 | McMaster | FINAL |
| **Narrow CF Tube** | McMaster 2040N14 | 2 | \$73.76 | McMaster | FINAL |
| **L Stock For Brackets** | McMaster 8982K525 | 1 | \$3.46 | McMaster | FINAL |
| **Steering Flat Plate** | SendCutSend Custom | 1 | \$280.75 | Send Cut Send | FINAL |
| **U Joint** | [Misumi U-Joint](https://us.misumi-ec.com/vona2/detail/U-Joint) | 1 | \$50.37 | Misumi | FINAL |
| **Standoffs** | McMaster 93538A101 | 1 | \$18.69 | McMaster | FINAL |