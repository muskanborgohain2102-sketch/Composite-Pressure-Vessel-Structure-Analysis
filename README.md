# Structural FEA of a Composite Pressure Vessel for Rocket Propulsion Applications

## Overview

This project presents the modelling and structural finite element analysis of a cylindrical pressure vessel representative of a rocket propulsion system, with the primary objective of evaluating graphite/epoxy composite laminates as alternatives to conventional metallic structures under high internal pressure loading. Two symmetric laminate configurations — **[0°/±45°/90°]s** and **[0°/±30°/±45°/90°]s** — were analysed and compared against structural steel as a baseline, with emphasis on hoop stress distribution, thickness sensitivity, and the influence of fibre orientation on load-carrying performance.

> **Note:** The thermal-structural and material characterization components of this research have been accepted for publication in the conference proceedings of **ICRAME 2025, NIT Silchar**. This repository presents the structural pressure analysis component only.

---

## Problem Statement

Despite growing adoption of composite materials in aerospace structures, the effect of fibre orientation on structural performance under realistic pressure loading conditions remains comparatively underexplored. This study addresses that gap by systematically comparing laminate configurations and quantifying the influence of ply orientation on hoop stress behaviour in a pressure-loaded cylindrical vessel.

---

## Methodology

### Geometry and Boundary Conditions

A thin-walled cylindrical vessel was modelled with the following parameters:

| Parameter | Value |
|---|---|
| Length | 100 mm |
| Inner Diameter | 110 mm |
| Outer Diameter | 114 mm |
| Internal Pressure | 50 MPa (radial) |
| Boundary Condition | Fixed support (one end) |

### Materials

- **Graphite/Epoxy Composite** — fibre volume fraction: 64 wt%, matrix: 36 wt%. Selected for its high specific stiffness, low density, and the ability to tailor mechanical properties through fibre orientation.
- **Structural Steel** — used as the validation baseline material due to its well-established, isotropic elastic properties, which make analytical comparison straightforward.

### FEA Setup

- Software: **ANSYS Workbench** (ACP + Static Structural)
- Element type: Shell elements (appropriate for thin-walled curved geometry)
- Two laminate configurations analysed using **Classical Lamination Theory (CLT)** to determine local stresses and strains, with global stresses computed using thin-walled pressure vessel theory

### Laminate Configurations

**[0°/±45°/90°]s** — 15 mm ply thickness, 7.5 cm total laminate thickness
- 0° fibres resist axial loads from internal pressure and thrust
- 90° fibres counteract hoop stresses and prevent radial expansion
- ±45° fibres provide shear resistance and improve damage tolerance

**[0°/±30°/±45°/90°]s** — 12 mm ply thickness, 8.4 cm total laminate thickness
- All of the above, with the addition of ±30° fibres for improved shear distribution, reduced stress concentration, and better fatigue resistance

---

## Mesh Convergence Study

To establish simulation reliability, a mesh convergence study was conducted on the structural steel model. Element count was progressively increased from **4,623 to 50,185 elements** (49,991 nodes). Total average deformation stabilised at approximately 30,000 elements; the final analysis was run at **50,185 elements** to ensure result accuracy and robustness.

---

## Validation of FEA Methodology

The FE model was validated against analytical thin-cylinder hoop stress calculations using the standard pressure vessel formula:

$$\sigma = \frac{pd}{2t}$$

where *p* = internal pressure, *d* = inner diameter, *t* = wall thickness.

Hoop stress was computed at seven wall thickness values and compared against simulation results:

| Thickness (cm) | FEA Result (MPa) | Theoretical (MPa) | Error (%) |
|---|---|---|---|
| 1 | 2927.4 | 2750.0 | 6.06 |
| 2 | 1451.5 | 1375.0 | 5.26 |
| 3 | 967.0 | 916.7 | 5.21 |
| 4 | 741.6 | 687.5 | 7.29 |
| 5 | 604.8 | 550.0 | 9.05 |
| 6 | 509.0 | 458.3 | 9.95 |
| 7 | 434.6 | 392.9 | 9.60 |

**Maximum deviation: ~10% | Deviation at working thickness (1 cm): ~6%**

The consistent agreement across all thickness values — with no systematic divergence — confirms that the FE model reliably captures hoop stress behaviour across the operating range. The slight over-prediction by ANSYS relative to thin-cylinder theory is expected, as shell FEA accounts for bending effects near the fixed boundary that the analytical formula does not. Hoop stress was also confirmed to vary linearly with internal pressure (50–120 MPa range), consistent with linear elastic thin-wall theory.

---

## Results

### Per-Ply Hoop Stress — Laminate [0°/±45°/90°]s

| Fibre Orientation | Max Hoop Stress (MPa) | Min Hoop Stress (MPa) |
|---|---|---|
| 0° | 2886.1 | 101.3 |
| 45° | 1864.6 | 67.8 |
| 90° | 1097.8 | 0.43 |

### Per-Ply Hoop Stress — Laminate [0°/±30°/±45°/90°]s

| Fibre Orientation | Max Hoop Stress (MPa) | Min Hoop Stress (MPa) |
|---|---|---|
| 0° | 3338.4 | 0.29 |
| 30° | 2691.3 | 0.29 |
| 45° | 2176.8 | 0.29 |
| 90° | 1368.9 | 0.34 |

The results confirm the fundamental composite mechanics principle that maximum stiffness is achieved when fibres are aligned with the loading direction — the 0° ply consistently shows the highest hoop stress capacity in both configurations.

### Laminate-to-Laminate Comparison

Introducing the additional ±30° ply orientations in [0°/±30°/±45°/90°]s produced consistent improvements across all fibre directions compared to [0°/±45°/90°]s:

| Fibre Direction | Strength Increase |
|---|---|
| 0° | +14% |
| 45° | +15% |
| 90° | +20% |

This improvement is attributed to more uniform load distribution across the laminate stack as the number of distinct orientations increases.

### Overall Hoop Stress Comparison (Full Laminate, 50 MPa)

| Material | Max Hoop Stress (MPa) |
|---|---|
| Structural Steel | 2927.4 |
| Graphite/Epoxy [0°/±45°/90°]s | 80.8 |
| Graphite/Epoxy [0°/±30°/±45°/90°]s | 72.1 |

*Note: This comparison reflects differences in stress distribution behaviour between isotropic and anisotropic materials under the same loading conditions, not a direct material strength comparison.*

---

## Conclusions

1. **Validation confirmed:** FEA results agreed with analytical thin-cylinder calculations within a maximum error of ~10%, and within ~6% at the primary working thickness, establishing confidence in the simulation methodology.

2. **Composite configurations outperform steel in stress distribution:** Both graphite/epoxy laminate configurations exhibited substantially lower and more evenly distributed hoop stress than structural steel under identical loading, indicating better structural efficiency for pressure vessel applications.

3. **[0°/±30°/±45°/90°]s is the superior laminate:** This configuration achieved 14–20% higher stress capacity across fibre directions compared to [0°/±45°/90°]s, driven by improved multi-directional load sharing from the additional ±30° plies.

4. **Fibre orientation is a critical design variable:** The systematic variation in hoop stress with ply angle — from maximum at 0° to minimum at 90° — demonstrates the importance of layup optimisation in composite pressure vessel design.

5. **Graphite/epoxy laminates are viable candidates** for replacing metallic components in propulsion-integrated rocket structures, with potential for significant mass savings while maintaining structural adequacy under mechanical loading.

---

## Tools and Methods

- ANSYS Workbench 2024 R1 (ACP + Static Structural)
- Classical Lamination Theory (CLT)
- Thin-walled pressure vessel theory (analytical validation)
- Shell element meshing

---

