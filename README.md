# Structural and Modal Analysis of a Toroidal Propellor

## Overview
This repository contains the structural and modal analysis of a toroidal propellor geometry developed for nano drone applications. The analysis was performed as a continuation of an M.Tech research project which was focused on noise reduction in nano drones through toroidal propellor design.

The optimized toroidal propeller, developed during the M.Tech research project, achieved a 51% reduction in acoustic signature (63 dB to 31 dB) with an 11% reduction in thrust compared to the baseline propeller. This repository focuses on evaluating the structural integrity and dynamic behaviour of the final design under operational loading conditions.

---

## Objectives
- Assess structural integrity of the toroidal propellor under operational rotational loading
- Identify critical stress regions and evaluate safety margins
- Determine natural frequencies and mode shapes to assess resonance risk at operating conditions

---

## Software

- ANSYS Workbench 2024
  - Static Structural
  - Modal Analysis
- SpaceClaim

---

## Material Properties
**Carbon Fibre (290 GPa) — Orthotropic**

| Property | Value | Unit |
|----------|-------|------|
| Density | 1800 | kg/m³ |
| Young's Modulus (X) | 290 | GPa |
| Young's Modulus (Y, Z) | 23 | GPa |
| Poisson's Ratio XY, XZ | 0.2 | — |
| Poisson's Ratio YZ | 0.4 | — |
| Shear Modulus XY, XZ | 9 | GPa |
| Shear Modulus YZ | 8.21 | GPa |
| Tensile Ultimate Strength | 400 | MPa |

S-N curve defined using tabular data with log-log interpolation.

---

## Boundary Conditions
- **Fixed Support** — applied at the hub root where the propellor attaches to the motor shaft
- **Rotational Velocity** — 262 rad/s (2500 RPM) applied about the Y-axis to simulate operational centrifugal loading

---

## Results

### Static Structural

| Parameter | Value |
|-----------|-------|
| Maximum Von Mises Stress | 41.18 MPa |
| Maximum Total Deformation | 1.0801 mm |
| Minimum Safety Factor | 3.6425 |

Maximum stress occurs at the blade root — expected due to highest bending moment at the fixed support. Von Mises stress of 41.18 MPa is well within the UTS of 
400 MPa, giving a safety factor of 3.6 — confirming structural feasibility of the toroidal geometry under operational loading.

---

### Modal Analysis

| Mode | Frequency (Hz) |
|------|---------------|
| 1 | 47.138 |
| 2 | 47.223 |
| 3 | 70.396 |
| 4 | 47.138 |
| 5 | 247.53 |
| 6 | 249.28 |

**Operating frequency at 2500 RPM = 41.67 Hz**

Modes 1 and 2 occur at 47.138 Hz and 47.223 Hz respectively, approximately 13% above the operating frequency. While this margin is acceptable, it warrants  attention during operation. Modes 3 and above occur at significantly higher frequencies and pose no resonance risk under normal operating conditions.

---

## Key Findings
- Toroidal propellor geometry is structurally feasible under operational rotational loading
- Maximum stress of 41.18 MPa is well below UTS of 400 MPa — safety factor of 3.6
- Natural frequencies are above operating frequency — no resonance under normal operation
- Modes 1 and 2 are closely spaced at 47 Hz, which suggests coupled bending modes due to 
toroidal symmetric geometry, which is similar to modes 3 and 4, and 5 and 6.
- Higher modes above 70 Hz pose no risk at 2500 RPM operating condition

---

## Repository Structure
```text
Structural-Analysis-of-Toroidal-Propellor/
├── README.md
├── LICENSE
├── geometry/
│   └── screenshots/
├── boundary_conditions/
│   └── screenshots/
├── results/
│   ├── static_structural/
│   │   ├── von_mises_stress/
│   │   ├── total_deformation/
│   │   └── safety_factor/
│   └── modal_analysis/
│       ├── mode_1/
│       ├── mode_2/
│       ├── mode_3/
│       ├── mode_4/
│       ├── mode_5/
│       └── mode_6/
└── material_properties/
└── screenshots/
```

