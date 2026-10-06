---
layout: project
title: Autosteer
description: Autonomous Steering System for Electric Car
image: /assets/images/AutosteerCAD.png
technologies: Autodesk Inventor, Ansys, Arduino IDE, C++, Manual Mill, 3D printing, Google Sheets
---
#### Overview 
The system is developed to allow the rack and pinion of an electric car competeing in Shell EcoMarathon to be manipulated via motor and engaged or disengaged via electromagnetic clutch. It interfaces with the rack and pinion via one half of the electromagnetic clutch being placed on the shaft that runs through the rack and pinion. A benchtop was also developed to test the system outside of the car with modeled force from tension and compression dampers.
![Figures]({{ "/assets/images/AutosteerinCar.png" | relative_url }})
![Figures]({{ "/assets/images/AutosteeronBenchtop.png" | relative_url }})

#### Terminology
* Electromagnetic clutch: when powered the 2 sides clamp together via magnet when unpowered they rotate separately.
* Benchtop: A testbed where the system can be run with simulated load before being tested in the car.
* 80-20: A grooved bar where a nut can be slid in and tightened at any desired position.
* Heat Set Inserts: Threaded metal pieces that can be melted into 3D prints to make threaded holes in the piece.

#### Design Requirements
The benchtop should allow testing of the system with both current rack and pinion and old rack and pinion so that the current rack and pinion could be assembled into the car and the benchtop used for continued testing. From feedback on last year’s design the system should have a quicker response time for exiting control by the system rather than the driver.
* 5 NM output needed to turn wheels at standstill - from spring scale testing on UC ‘ 24 with person in car
* 11.06 NM output needed to turn wheels from standstill from calculations for UC ‘26
* 1:5 Gear ratio - 15 Nm output torque

#### Potential Designs 
One of the main questions for this gearbox compared to last year’s gearbox is on which side of the gearbox should the clutch be. If the clutch is on the driver side the clutch needs to be stronger, but there will be no movement after the clutch is disconnected.  If the clutch is on the gearbox side then it can be weaker, but will move some after the clutch is disconnected. 
2 stage gear box: Larger footprint, can use only 1 size of stock so can be cheaper, has been done in previous years
1 stage gear box: requires the use of gears with different size shafts to achieve the desired gear ratio of 1:5 due to the small size of smaller gear needed to achieve the ratio with the largest gear available from West Coast Products. Smaller footprint, maybe lighter
Types of force simulation on the benchtop:
* Integrated compression and tension dampers: Best overall option to accurately model the force and even have options to have variable resistance, but expensive
* force modeled with 2 compression dampers and 2 tension dampers: can torque apply an internal torque but much cheaper

#### Selected Design 
The clutch is placed on the driver side of the gearbox so that there is faster response between disconnecting the clutch and the driver having full control over steering based on feedback from previous year’s design. The gearbox is a 1 stage gearbox despite the slightly higher cost due to the decreased footprint in the car and decreased weight. The force simulation is done by a combination of 2 tension and 2 compression dampers compared to 2 combined dampers despite the possibility of an internal torque due to the price difference of approximately $100 per damper. 

#### Detailed CAD And Design Explanation
![Figures]({{ "/assets/images/postfdr.png" | relative_url }})
![Figures]({{ "/assets/images/changedgearbox.png" | relative_url }})
![Figures]({{ "/assets/images/benchtopcad.png" | relative_url }})

The autosteer system consists of connecting a nema 23 stepper motor seated in a 36 printed mount designed to fit the exact shape of the motor underneath, connected to a ⅜” hex shaft machined down to round with a keyway in it via a shaft coupler. The keyway has the set screw of the shaft coupler tightened into it since we did not want to risk altering the shaft of the motor since it cannot be removed. This ⅜” hex shaft has a 14 tooth gear interfacing with a 70 tooth gear that is on a ½” hex shaft machined down to round with a keyway and 4mm key in it. This keyway lines up with a keyway on the gearbox side of the clutch which is connected to the gearbox via heat set inserts. This then connects to the other side of the clutch magnetically when engaged. This other side of the clutch is mounted with a keyway on the drive shaft on the back side of the rack and pinion. The gearbox was designed to be used in 2 different orientations to simplify spacing on the benchtop, it could be used oriented on its side. This would allow there to be a much smaller spacing of the rack and pinion housing off the benchtop which means it could be easily 3D printed. This small 3D print would also allow the easier switching between the current and old rack and pinion. The brackets have holes tapped on either side that the dampers thread into and on the inside these brackets are bolted through the rack and pinion and on the outside they are attached to 80-20s via 2 holes to minimize any internal torque that might occur.  The design had to be changed at the end of the semester when integrating into the car due to the shaft being offset from the position in CAD (likely key offset further from autosteer than it was in CAD). To make up for this the autosteer system was redesigned to have the holes offset to to make up for the gap. This led to the gearbox being redesigned in 2 halves to simplify assembly due to some of the holes that had originally been in front of the gearbox now being inside the outer walls of the gearbox. When the redesign was done to fix spacing the ability to turn the gearbox sideways to test on the benchtop was removed since benchtop testing had been completed and it allowed for more support to compensate for the new gaps in the gearbox to screw in the screws attaching the system to the steering plate between the walls of the gearbox. This spacing difference also led to a small change in the motor mount through the implementation of an overhang to compensate for how much of the gearbox spacing assembly had to stick underneath where the motor mount had been. This gearbox redesign also integrated a backup mount for the steering angle sensor using heat set inserts on the gearbox side. This mount is a backup because if mounted on the gearbox side we only get the steering angle data when autosteer is engaged. This was designed since the steering angle sensor can only be removed by disassembling the rack and pinion assembly this year and IGVC needed the same sensor (and theirs took time to arrive) so if it was going back and forth it could easily be screwed into the heat set inserts and removed quickly after testing. Based on testing results this mounting on the gearbox side  seems like it may produce better data but that should be further investigated.

#### Off the Shelf Component Selection and Justification
* L Bracket stock: Buying from McMaster Carr, $10.46 and decreases machining time compared to rectangular stock
* Gears: we can’t make at the required precision and only $35.98

#### Interfacing 
The autosteer system will screw into the steering plate with 4 mounting holes on the gearbox and 4 on the motor mount. One half of the clutch will be on the drive shaft behind the rack and pinion. The other half of the clutch will engage with it and spin together when powered.

#### Analysis
**Boundary Conditions**
Cylindrical Supports where bearings are, fixed supports at screws.  These simulate reality relatively well.
**Mesh and Convergence**
The ANSYS could be improved by adding internal forces due to the gears, however, as it is a 3D print the ANSYS was not particularly the most helpful tool due being anisotropic and having material properties easily altered by infill print direction. The ANSYS was mostly used as a quick check to make sure everything looked reasonable.
**Results and Optimization**
Due to being a 3D print nothing was changed after ansys but it was checked for safety factor which is 2,599.
![Figures]({{ "/assets/images/AutosteerAnsys.png" | relative_url }})

#### Bill of Materials

| Part | Link | Sku | # packages needed | Price per package | Vendor |
| --- | --- | --- | --- | --- | --- |
| 1/4 20 screws | Already Have | 90128A242 | 1 | $12.58 | McMaster |
| m6 screws | [Link](https://www.mcmaster.com/products/screws/socket-head-screws-2~/alloy-steel-socket-head-screws-8/length~18-mm/thread-size~m6-2/?s=m6+screws) | 91274A135 | 1 | $4.70 | McMaster |
| 3/8" Hex Shaft | [WCP](https://wcproducts.com/) |  |  |  | WCP |
| .5" Hex shaft | [WCP](https://wcproducts.com/) |  |  |  | WCP |
| 4\*4 mm Key | [Link](https://www.mcmaster.com/products/key-stock/machine-keys-4~/machine-keys-3~~/) |  | 1 | $4.77 | McMaster |
| 3/8 in hex bearing | Already Have |  |  |  |  |
| .5 in hex bearing | Already Have |  |  |  |  |
| Shaft Coupler | [Link](https://www.mcmaster.com/products/shaft-couplers/shaft-couplings-1~/set-screw-shaft-couplings/shaft-diameter~8-mm/) | 5395T211 | 1 | $7.32 | McMaster |
| Motor | Already Have |  |  |  |  |
| Heat Set Inserts | [Link](https://www.mcmaster.com/products/inserts/threaded-insert-type~heat-set/heat-set-inserts-for-plastic-7/thread-size~m6/) | 94459A210 | 1 | $8.91 | McMaster |
| 70 tooth aluminum gear | [Link](https://wcproducts.com/collections/belts-chain-gears/products/aluminum-hex-bore-gears) | 0172 | 1 | $24.99 | WCP |
| m5 screws | [Link](https://www.mcmaster.com/products/screws/socket-head-screws-2~/alloy-steel-socket-head-screws-8/length~18-mm/?s=m6+screws) | 91502A166 | 1 | $9.67 | McMaster |
| 14 tooth aluminum gear | [Link](https://wcproducts.com/collections/belts-chain-gears/products/aluminum-hex-bore-gears) | 0680 | 1 | $10.99 | WCP |
| Clutch | Already Have |  |  |  |  |
| Hall Effect Sensor | Already Have |  |  |  |  |
| Benchtop |  |  |  |  |  |
| Base Plate Stock | [Link](https://www.mcmaster.com/products/aluminum-plates/thickness~1-4/oversized-multipurpose-6061-aluminum-sheets/) | 89155K11 | 1 | $12.11 | McMaster |
| Nuts for 80-20s | Already Have |  |  |  |  |
| 80 20s | Already Have |  |  |  |  |
| Tension Damper | [Link](https://www.guden.com/itemdetail/GNE53-J) | GNE53-J | 2 | $18.24 | Guden |
| Compression Damper | [Link](https://www.guden.com/itemdetail/GNC53-D) | GNC53-D | 2 | $18.24 | Guden |
| L bracket Stock | [Link](https://www.mcmaster.com/products/stock/shape~90-angle/aluminum-3~/multipurpose-6061-aluminum-90-angles~~/wall-thickness~1-4/wall-thickness~0-250/wall-thickness~0-25/outside-height~1-1-4/) |  | 1 | $10.46 | McMaster |

#### Manufacturing Plan
Brackets to attach dampers to the rack and pinion on the benchtop will be put on the mill to face, remove inner fillet, and drill holes. Those holes will then be tapped by hand to thread the dampers on.
Baseplate for Benchtop: drilled on drill press in composites using 3d printed mounts as guides
½” Hex shaft: Lathe to circular on end then put on mill to add keyway
⅜”Hex Shaft:  Lathe to circular on end then put on mill to add keyway
Gearbox: 3D printed
Motor Mount: 3D printed 

#### Assembly Plan
The system can be assembled and then screwed into the car except for the driver side of the clutch. The driver side of the clutch either has to be put in before the rest of the system, is put in the car or with the rack and pinion disassembled to the point that the drive shaft can be shifted back, put the clutch on, and then reassembled shifted forwards. After the design change to split the gearbox in half the assembly of the gearbox is quite simple consisting of putting the bearings in both sides on the hydraulic press, putting the shafts in the bearings on 1 side, putting on spacer gear spacer on each shaft, and finally connecting the 2 sides of the gearbox via 4 screws , 1 in each corner.  

#### Testing Plan
Test print and proof that press fitting the bearings would be sufficient was done by creating a large 3d printed plate with a variety of tolerances to find the correct amount of tolerance and then apply force one press fit to ensure that the bearings would not be easily removed. Both hexagonal and circular holes were tested finding that zero tolerance on the 3d print worked with the bearing and could not be easily removed. These were able to be pressed in with force by hand but due to the thicker nature of the gearbox’s geometry the bearings were hydraulic pressed in for the final design with the same tolerancing. 

![Figures]({{ "/assets/images/testprint.png" | relative_url }})

#### Project Reflection and Other Work
If I were to start from scratch on this project I would firstly do more extensive hand calcs for and  buy a new clutch as this clutch is 6NM and was bought in a previous year when the clutch was on the other side of the gearbox which required a smaller clutch, so with this year’s redesign with the clutch on the driver side it was no longer strong enough. We had not bought a new one as it worked on the benchtop and in initial tests in the car, however when the car is placed down onto the floor and not propped up the clutch decouples and does not have enough force to move the wheels. We should have verified calculations from previous years about how much force it takes to move the rack and pinion with the changes to our steering geometry with a force gauge so we could have bought a new clutch before we went to integrate the system with telemetry.  In future years I would also include a 1:1 gear ratio connection to simplify taking autosteer in and out of the car. This would consist of having the same sized gear on the drive shaft and a new shaft with the drive side of the clutch on it. This would allow autosteer to be lifted out of the car after being unscrewed without having to change anything on the rack and pinion side. I would definitely recommend having the gearbox split in half again next year as it greatly simplified the assembly process, but would ensure the spacing is exact the first time so that there don’t need to be holes in the front of the gearbox to screw it into the steering plate between the walls of the gearbox (which happened this year due to incorrect spacing with the drive shaft that made the driverside screws connecting autosteer to the steering plate difficult to screw in.

#### References
* EM Clutch: https://peacosupport.com/electromagnetic-clutches/electromagnetic-clutch-dc-24v 
* Motor: https://www.amazon.com/STEPPERONLINE-Stepper-Bipolar-57x57x113mm-Engraving/dp/B0CG58KY17/ref=sr_1_1?sr=8-1 
* Steering Angle Sensor: https://www.farnell.com/datasheets/4165599.pdf 
* Code I wrote and tested Autosteer with on benchtop to run to different positions w/ PID: https://github.com/Lydia754/CEV_Autosteer_2026 
