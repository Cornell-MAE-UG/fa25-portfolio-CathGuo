---
layout: project
title: Instrumented Torque Wrench Design
description: Strain Gauge-Based Torque Measurement System
technologies: [Autodesk Fusion 360, ANSYS FEM, MATLAB, Mechanical Design, Stress Analysis]
course: MAE 3270 - Mechanical Properties of Materials
image: /assets/images/torque_wrench.png
---

As part of my mechanical engineering curriculum at Cornell University, I designed and analyzed an instrumented torque wrench rated for 600 in-lbf using integrated analytical methods and finite element analysis (FEM). This project synthesized materials selection, fracture mechanics, fatigue analysis, strain gauge instrumentation, and structural optimization.

![Torque wrench CAD model with dimensions]({{ "/assets/images/torque_wrench_dimension.png" | relative_url }}){: .inline-image-c}

(dimensions are in inch)

## Design Overview

The project required designing a non-ratcheting, 3/8-inch drive torque wrench that transduces torque through strain gauges bonded to the handle surface. The primary challenge was optimizing the wrench geometry and material to maximize sensor sensitivity (voltage output) while meeting strict safety requirements for static loading, crack growth, and fatigue failure.

**Key Design Requirements:**
- Minimum 1.0 mV/V output at rated torque (600 in-lbf)
- Safety factor ≥ 4.0 for yield/brittle failure
- Safety factor ≥ 2.0 for crack growth (0.04 inch initial crack)
- Safety factor ≥ 1.5 for fatigue (10⁶ cycles, fully reversed loading)
- Material limited to steel, aluminum, or titanium alloys

<div style="clear: both;"></div>

## Material Selection & Optimization

### Material Selection Strategy

I selected **7075-T6 Aluminum** for its optimal combination of high strength and low elastic modulus. The key insight was recognizing that strain output is inversely proportional to Young's modulus (ε = σ/E), making aluminum's modulus of 10.5×10⁶ psi approximately three times better than steel's 30×10⁶ psi for generating measurable strain at safe stress levels.

**Material Properties:**
- Young's Modulus: 10.5×10⁶ psi
- Tensile Strength: 71.8 ksi
- Fracture Toughness: 24.3 ksi√in
- Fatigue Strength (10⁶ cycles): 28 ksi
- Poisson's Ratio: 0.33

### Dimensional Optimization

Through iterative MATLAB calculations, I optimized the wrench dimensions to balance competing objectives:

**Final Design Dimensions:**
- Total length: 16 inches
- Length (L): 15 inches
- Width (h): 0.8 inches
- Thickness (b): 0.5 inches
- Gauge location (c): 0.5 inches from drive

The dimensional optimization involved multiple strategic changes. Reducing the length from 16 to 15 inches increased the bending stress and strain throughout the handle for the same applied torque (since moment arm is proportionally shorter). Increasing the width slightly from 0.75 to 0.8 inches provided additional structural capacity to compensate for the shorter length while maintaining safety factors. Most critically, moving the gauge placement closer to the drive (0.5 in vs 1.0 in baseline) positioned it in a higher moment region, significantly boosting strain output. Combined with aluminum's lower elastic modulus, these optimizations resulted in 2.7× higher strain output (1,019 microstrain vs 375 microstrain) compared to the steel baseline design while maintaining all required safety factors.

<div style="clear: both;"></div>

## Analytical Design Process

### Hand Calculations

I developed a MATLAB script to perform rapid design iterations, calculating:
- Maximum bending stress using beam theory (σ = 6M/bh²)
- Strain at gauge location accounting for moment distribution
- Stress intensity factor for fracture analysis (K_I = 1.12σ√πa)
- Safety factors for all failure modes
- Voltage output from half-bridge strain gauge configuration

The analytical approach enabled quick exploration of the design space, identifying promising material-geometry combinations before committing to detailed FEM analysis.

**Key Analytical Results:**
- Maximum normal stress: 11.25 ksi (beam theory prediction)
- Load point deflection: 0.201 inches
- Strain at gauge: 1,036 microstrain
- Predicted output: 1.04 mV/V (exceeds 1.0 mV/V requirement)

![Total deformation contour]({{ "/assets/images/torque_wrench_max_deformation.png" | relative_url }}){: .inline-image-c}

### Safety Factor Analysis

All safety factors comfortably exceeded minimum requirements:
- **Strength:** 6.38 (required ≥ 4.0) 
- **Crack growth:** 5.44 (required ≥ 2.0) 
- **Fatigue:** 2.49 (required ≥ 1.5) 

Fatigue emerged as the limiting constraint, consistent with design theory for cyclically loaded components. This validated the design approach and confirmed that further dimension reduction would risk fatigue failure before static overload.

<div style="clear: both;"></div>

## Finite Element Analysis

### FEM Validation & Refinement

Using ANSYS, I built a detailed finite element model of the final design to validate analytical predictions and capture stress concentrations not visible to simple beam theory.

![Loads and boundary conditions applied to FEM model]({{ "/assets/images/torque_wrench_load_and_boundary.png" | relative_url }}){: .inline-image-c}

**FEM Setup:**
- **Boundary conditions:** Fixed constraint on upper 0.4 inches of drive block
- **Loading:** 40 lbf lateral force at handle end (equivalent to 600 in-lbf torque)
- **Mesh:** Refined mesh with convergence study
- **Element type:** 3D solid elements with midside nodes

The FEM analysis revealed important details:
- **Nominal stress** in the gauge region: 11.24 ksi (good agreement with 11.25 ksi hand calculation)
- **Peak stress** at drive corner: 58.22 ksi (stress concentration factor ~5.2×)
- **Load point deflection:** 0.323 inches (higher than analytical due to drive compliance)
- **Strain at gauge:** 1,019 microstrain (1.0186×10⁻³ in/in)

![Normal stress contour]({{ "/assets/images/torque_wrench_max_normal_stress.png" | relative_url }}){: .inline-image-c}

<div style="clear: both;"></div>

![Normal strain contours in longitudinal direction]({{ "/assets/images/torque_wrench_normal_strain_contour.png" | relative_url }}){: .inline-image-c}

### Normal Strain Distribution

The normal strain contour plot (shown in the strain gauge measurement direction) reveals the expected bending strain distribution. The -y of the beam experiences positive strain (tension, yellow-green regions showing ~1,900 microstrain maximum). 

At the strain gauge location (0.5 inches from the drive), the strain is approximately 1,019 microstrain, which matches the probe measurement. The strain gradient along the beam length confirms that positioning the gauge closer to the drive significantly increases the measured strain compared to locations further from the fixed end. 

<div style="clear: both;"></div>

![Maximum principal stress distribution]({{ "/assets/images/torque_wrench_max_principal_stress.png" | relative_url }}){: .inline-image-c}

### Maximum Principal Stress Analysis

The maximum principal stress contour reveals critical stress concentrations at the drive-handle interface. While most of the beam experiences relatively low stress (blue regions, <13 ksi), the sharp corner where the rectangular handle meets the square drive block shows a dramatic stress concentration reaching 120.9 ksi (red region). 

This 5.2× stress amplification factor cannot be predicted by simple beam theory and demonstrates why FEM analysis is essential for real-world component design. The stress concentration is the most likely location for fatigue crack initiation, despite the nominal beam stresses being well within safe limits. This finding emphasizes the importance of including geometric features like fillets in production designs to reduce stress concentration factors and improve fatigue life.

<div style="clear: both;"></div>

### Strain Gauge Instrumentation

**Configuration:** Half-bridge arrangement with two active gauges
- Gauge 1: -y surface (tension)
- Gauge 2: +y surface (compression)
- Location: 0.5 inches from drive centerline

**Sensitivity Calculation:**
Using FEM strain data (ε = 1,019 με) and gauge factor (GF = 2.0):
- Output = GF × ε / 2 = 2.0 × 0.001019 / 2 = 1.019 mV/V
- **Performance:** Exceeds 1.0 mV/V requirement by 1.9%

The half-bridge configuration provides temperature compensation and doubles sensitivity compared to a quarter-bridge (single gauge) setup, ensuring robust torque measurement across varying environmental conditions.

**Selected Gauge:** CEA-06-125UN-350 (Micro-Measurements)
- Overall length: 0.38 inches
- Overall width: 0.19 inches
- Resistance: 350 Ω
- Fits comfortably at c = 0.5 in location with adequate bonding area

<div style="clear: both;"></div>

## Key Findings & Design Insights

### Beam Theory vs. FEM Comparison

**Stress Analysis:**
The hand-calculated maximum normal stress (11.25 ksi) agreed well with FEM results in the uniform beam section (11.24 ksi). However, FEM revealed a critical stress concentration of 58.2 ksi at the sharp corner where the handle meets the drive block, a ~5× amplification factor that beam theory cannot predict. This stress concentration is the most likely initiation site for fatigue cracks and validates the importance of safety factors and FEM analysis for real-world designs.

**Deflection Analysis:**
FEM predicted 0.323 inches of load point deflection compared to 0.201 inches from beam theory. This discrepancy arises because beam theory assumes a perfectly rigid fixed support, while the actual drive block has finite stiffness and contributes additional compliance. The FEM model captures the complete structural response, including drive deformation, making it more accurate for predicting real-world behavior.

**Strain Measurement:**
Both methods predicted approximately 1,000-1,100 microstrain at the gauge location, demonstrating that simple beam theory provides excellent estimates for strain in uniform sections away from geometric discontinuities. This validates the analytical approach for preliminary design iterations.

### Design Optimization Lessons

1. **Material Selection is Critical:** Aluminum's low modulus provided 3× strain amplification compared to steel at equivalent stress levels, enabling the sensitivity requirement to be met with conservative safety factors.

2. **Gauge Placement Strategy:** Moving the gauge closer to the drive (c = 0.5 in vs baseline 1.0 in) doubled the local bending moment and strain, significantly improving sensitivity without compromising safety.

3. **Competing Objectives:** The design required careful balancing—smaller cross-sections increase sensitivity but reduce safety factors. Fatigue became the active constraint, naturally limiting further size reduction.

4. **Stress Concentrations Matter:** While beam theory sufficed for nominal design, FEM was essential for identifying the 5× stress concentration at the drive corner, which would dominate failure initiation in service.

## Technical Skills Demonstrated

Through this comprehensive design project, I developed proficiency in:
- **Materials selection** based on mechanical property requirements
- **Analytical stress analysis** using beam theory and fracture mechanics
- **Fatigue life prediction** using S-N curves and stress-based methods
- **Strain gauge instrumentation** and signal conditioning principles
- **CAD modeling** in Fusion 360 with engineering documentation
- **Finite element analysis** in ANSYS with mesh convergence studies
- **Design optimization** with multiple competing constraints
- **MATLAB scripting** for automated parametric design iteration
- **Technical communication** through engineering drawings and analysis reports

## Design Impact & Applications

This torque wrench design demonstrates engineering fundamentals applicable to:
- **Precision instrumentation:** Load cells, pressure transducers, force sensors
- **Automotive tools:** Calibrated torque wrenches for critical fastener applications
- **Aerospace assembly:** Torque measurement for structural joint integrity
- **Manufacturing quality control:** Automated torque verification systems
- **Biomedical devices:** Force measurement for surgical instruments

The integration of analytical and computational methods reflects modern engineering practice, where rapid hand calculations guide initial design while FEM provides validation and reveals complex phenomena beyond simplified theory.

## Project Details

**Course:** MAE 3270 - Mechanical Properties of Materials, Fall 2025  
**Institution:** Cornell University  
**Tools:** MATLAB, Autodesk Fusion 360, ANSYS FEM  
**Analysis Methods:** Beam theory, fracture mechanics, fatigue analysis, finite element method  
**Deliverables:** Technical report, CAD model, FEM analysis, design calculations

---

This project represents the synthesis of materials science, solid mechanics, and computational analysis—fundamental skills for mechanical engineers designing safe, reliable, high-performance components across all industries.