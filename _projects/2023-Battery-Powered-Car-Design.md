---
layout: project
title: Battery-Powered Car Design
description: ENGRI 1170 Final Project - Dual-Mode Competition Vehicle
technologies: [Autodesk Fusion 360, Laser Cutting, Band Saw, Drill Press, Gearbox Design, DC Motors, Circuit Design]
image: /assets/images/Sacabam-chassis-render.png
---

For the ENGRI 1170 final project, our team designed and manufactured a battery-powered car optimized for both high speed and high pulling force. Named "Sacabam" after the prehistoric fish that inspired its aesthetic, the car features two distinct operating modes with separate wheel systems and gearboxes.  

## Design Concept

![Actual Sacabam]({{ "/assets/images/Sacabam-actual.jpg" | relative_url }}){: .inline-image-r}

The design challenge required balancing two competing objectives: maximum speed and maximum pulling force. Rather than compromising on either, we designed a dual-mode vehicle that could be flipped between configurations:

- **High-Speed Mode**: 9 cm diameter wheels with 38.2:1 gearbox for maximum translational velocity
- **Pulling Force Mode**: Tank treads with 344.2:1 gearbox for maximum torque output

The rectangular frame (12.5 × 30 × 13.5 cm) accommodated both wheel systems on opposite sides, allowing quick mode switching by flipping the car.

## Design Development

Our design process began with brainstorming sessions exploring various concepts. Key design decisions included:

**Frame Geometry**: We chose a rectangular shape to accommodate both wheel systems, rejecting triangular designs that would have required connected wheel systems.

**Material Selection**: Originally planning to use wood, we switched to laser-cut acrylic after calculating that it would provide better strength while staying within the 800g weight limit. The acrylic was more sturdy, aesthetically pleasing, and fit the fish theme better.

**Gearbox Selection**: For high speed, we selected the 38.2:1 ratio for maximum RPM with sufficient torque for acceleration. For pulling force, we chose 344.2:1 (second-highest torque option) based on expected car weight rather than the maximum 488.3:1.

![Pulling force mode]({{ "/assets/images/Sacabam-PF.png" | relative_url }}){: .inline-image-l}

## Manufacturing Process

The car frame consisted of four laser-cut acrylic plates designed to fit together like puzzle pieces. Manufacturing steps included:

1. **Gearbox Assembly**: Built two separate gearbox configurations for each mode
2. **Laser Cutting**: Cut acrylic frame pieces with precise dimensions for assembly
3. **Component Integration**: Mounted motors, battery box, and switches
4. **Wheel Installation**: Attached 90mm Pololu wheels for speed mode and tank treads for pulling mode
5. **Aesthetic Finishing**: Added removable outer boards featuring the Sacabambaspis cartoon

<div style="clear: both;"></div>

## Design Modifications

Several adjustments were made during manufacturing:

**Width Reduction**: The tank tread axles were shorter than expected, requiring us to trim the car's width to prevent frame collision.

**Battery Placement**: Originally planned for the bottom (in speed mode) to lower the center of gravity, but moved to center for better wiring access.

**Removable Panels**: Made outer aesthetic boards removable to allow battery replacement during competition.

## Technical Analysis

### Pulling Force Calculations

Using stall torque and gearbox ratio:
- Gear Ratio: 344.2:1
- Stall Torque: 1.362 × 10⁻² Nm
- Wheel Radius: 0.02 m
- Coefficient of Friction (tank treads): 0.839

**Theoretical Max Pull Force**: 234.4 N (limited by friction to 5.74 N)  
**Actual Max Pull Force**: 5.07 N  
**Accuracy**: 86.8% (13.2% error)

### Velocity Calculations

Using motor characteristics and gearbox ratio:
- Gear Ratio: 38.2:1
- Wheel Radius: 0.045 m
- Coefficient of Friction (wheels): 0.087

**Theoretical Max Velocity**: 3.14 m/s  
**Actual Average Velocity**: 1.94 m/s  
**Accuracy**: 61.8% (38.2% error)

The velocity error was primarily due to wheel misalignment causing the car to drift and collide with the wall during the race.

## Competition Results

**Speed Test**:
- Best Time: 6.17 seconds (12 m course)
- Average Velocity: 1.94 m/s

**Pull Test**:
- Best Pull Force: 1.14 lbf
- Best Normalized: 0.00163 lbf/g
- Won two head-to-head pulling competitions

## Challenges & Lessons Learned

### Wheel Alignment Issues
The front wheels of the high-speed mode wouldn't stay straight, causing the car to veer right. This consumed significant time and prevented planned testing of alternative gearbox ratios.

### Time Management
Unexpected alignment issues pushed back our schedule, eliminating planned testing and modification phases. We had to attend open studio sessions and work in dorms to complete manufacturing.

### Sources of Error
- Friction between axles and frame (not accounted for in calculations)
- Wheel misalignment causing wall collisions
- Slipping between wheels and tank treads
- Non-horizontal pulling angle during force tests

## Potential Improvements

If redesigning the car, we would:
- Add more wheels to the tank treads for increased friction coefficient
- Use thicker wheels for speed mode to reduce alignment sensitivity
- Grease axle connections to reduce friction losses
- Test both 38.2:1 and 12.7:1 gearboxes to verify optimal selection
- Allow more time for testing and iteration

## Team Collaboration

Working with teammates Nuo Xiang Yan and Yawen Lin, we:
- Held weekly meetings to coordinate progress and resolve issues
- Divided work based on individual schedules and availability
- Collaborated on design decisions through brainstorming sessions
- Supported each other through manufacturing challenges

## Project Details

**Course:** ENGRI 1170 - Introduction to Mechanical Engineering  
**Date:** December 2023  
**Team:** Yunting Catherine Guo, Nuo Xiang Yan, Yawen Lin  
**TA:** Mehali Desai  
**Final Weight:** 697.6 g  

---

This project taught valuable lessons about the complete engineering design cycle - from concept development through manufacturing to testing - while working within real constraints of budget, materials, weight limits, and timeline. The experience highlighted the importance of allowing buffer time for unexpected issues and the value of thorough testing before final competition. 