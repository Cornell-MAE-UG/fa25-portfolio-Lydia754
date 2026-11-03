---
layout: project
title: Steering Linkages, Steering Wheel Supports, Steering Flat Plate
description: Cornell Electric Vehicles 2026 Projects (steering lead)
image: chunk-0-img-0.jpeg
technologies: Autodesk Inventor, Ansys
---

## Overview

This year I am steering lead for the mechanical subteam of Cornell Electric Vehicles, I have 3 main projects alongside managing interfacing and design for the steering sub-projects. These projects are all for my steering subsystem of mechanical design for Cornell Electric Vehicles, which competes in the Shell Eco-marathon. 

### Core Projects:
1. **Steering Linkages:** Including Ackermann calculations and Finite Element Analysis (FEA).
2. **Steering Flat Plate:** Designed to allow more precise mounting connections and pocketed based on mounting holes for each project. Repeated Ansys modeling was performed to check deflection under main loading conditions (bump, brake, turn) to ensure pocketing results in minimal deflection *(currently undergoing finalization due to auto-brake and acceleration pedal mounting hole revisions)*.
3. **Steering Wheel Supports:** Redesigned following a baseplate redesign that removed wheel wells for simpler manufacturing. This change removed previous connection points for the steering wheel structure and decreased resistance to bending. The new design features a truss structure positioned above the pedals, reducing the moment arm associated with the supports compared to the previous design.

---

## Steering Subsystem Geometry & Architecture

### System Architecture Overview
![Overall Steering Architecture](assets/steering_architecture_overview.png)

---

## Steering Linkages

![Steering Linkage Assembly](assets/steering_linkages_top_view.png)

### Goals and Rule Requirements
- [x] Achieve close to pure Ackermann geometry.
- [x] Optimize Ackermann for a $10\text{ m}$ turning radius.
- [x] Achieve $4.5\text{ m}$ turning radius minimum capability.
- [x] Prevent interfacing issues with brake and accelerator pedals.
- [x] Implement a steering plate for easier, precise hole spacing and assembly.
- [x] Two-hand operation.
- [x] Steering radius $< 6\text{ m}$.
- [x] Minimal mechanical play.

### Design Parameters
* **Tie Rod Length:** $13.27\text{ in}$
* **Target Ackermann Percentage:** $104\%$

---

## Mathematical Analysis & Calculations

### Ackermann Calculations

#### Pure Inner Wheel Turning Radius
$$R_i = \sqrt{\left(R - \frac{w}{2}\right)^2 + L^2}$$

$$R_i = \sqrt{\left(6 - \frac{0.44}{2}\right)^2 + 1.502^2} = 9.7815\text{ m}$$

#### Pure Outer Wheel Turning Radius
$$R_o = \sqrt{\left(R + \frac{w}{2}\right)^2 + L^2}$$

$$R_o = \sqrt{\left(10 + \frac{0.44}{2}\right)^2 + 1.502^2} = 10.0431\text{ m}$$

#### Theoretical Steering Angles
* **Inner Steering Angle ($\delta_i$):**
  $$\delta_i = \sin^{-1}\left(\frac{L}{R_i}\right) = \sin^{-1}\left(\frac{1.502}{9.7815}\right)$$

* **Outer Steering Angle ($\delta_o$):**
  $$\delta_o = \sin^{-1}\left(\frac{L}{R_o}\right) = \sin^{-1}\left(\frac{1.502}{10.0431}\right) = 8.269^\circ$$

#### Ackermann Percentage Evaluation
$$\text{Ackermann } \% = \frac{(\delta_i - \delta_o)_{\text{actual}}}{(\delta_i - \delta_o)_{\text{ideal}}} \times 100$$

From CAD Sketch:
* $\delta_i = 9.00^\circ$
* $\delta_o = 8.39^\circ$

$$\text{Ackermann } \% = \frac{9.00 - 8.39}{8.833 - 8.269} \times 100 = 109.929\% \approx 110\%$$

*Note: Ackermann Steering is calibrated at $110\% \text{ @ } 10\text{ m}$. Actual target calculation is revised to $104\%$ due to the suspension-tierod interface being moved closer to the rack and pinion to resolve packaging issues.*

---

### Pinion Travel ($4.5\text{ m}$ Turn Radius Requirement)

$$\tan \delta = \frac{L}{R}$$

For $L = 1.50\text{ m}$ and $R = 4.5\text{ m}$:
$$\delta = 18.46^\circ$$
$$\theta_r = 28.46^\circ + 18.46^\circ = 46.88^\circ$$

$$y = r \cdot \sin(46.8^\circ) - \sin(28.4^\circ)$$
$$\Delta y = 72.4\text{ mm} = 2.85\text{ in} \quad \text{(per side)}$$

* **Total Required Rack Travel:** $\ge 5.7\text{ in}$

---

## Structural Analysis & Simulation (FEA)

### Tie Rod FEA
![Tie Rod Finite Element Analysis](assets/tie_rod_fea_analysis.png)

* **Load Condition:** $70.62\text{ lbf}$ applied axially from rack and pinion.
* **Material:** Aluminum 6061
* **Factor of Safety (FOS):** 15
* **Max Deformation:** $0.00298\text{ mm}$

---

## Steering Wheel Supports

![Steering Wheel Support Structure](assets/steering_wheel_support_cad.png)

### Design Strategy & Revisions
This design replaces previous iterations that anchored to a carbon fiber tube spanning between the wheel wells (removed following the baseplate redesign). 

An initial design attempted to anchor the supports to the aerodynamic side shell; however, hand calculations revealed excessive forces for non-load-bearing aero panels. The final iteration builds down directly to the carbon fiber baseplate, which is thicker and engineered for structural loads. The steering wheel shaft interfaces with the rack and pinion via a U-joint.

### Analysis & Hand Calculations
* **Steering Torque:** $12\text{ N}\cdot\text{m}$
* **Max Moment at Support:** $14\text{ N}\cdot\text{m}$

---

## Steering Flat Plate Analysis

![Steering Flat Plate Deflection FEA](assets/steering_flat_plate_fea.png)

### Design & Function
The primary objective of the steering flat plate is to establish exact hole placements across multiple subsystem components. Direct drilling into the carbon baseplate introduces positioning errors, which historically caused assembly inefficiencies.

* **Plate Thickness:** $0.25\text{ in}$
* **Hardware:** Pressed with $\frac{1}{4}\text{-}28$ flush nuts
* **Offset:** Elevated $0.25\text{ in}$ off the baseplate via side and center standoffs.
* **Factor of Safety (FOS):** 15
* **Max Total Deformation (FEA):** $0.11236\text{ mm}$

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