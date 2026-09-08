# 🔋 Mica Thermal Isolation in a Lithium-Ion Battery Pack

<p align="center">
  <img src="https://img.shields.io/badge/ANSYS-2025%20R1-red?style=for-the-badge" alt="ANSYS 2025 R1">
  <img src="https://img.shields.io/badge/Analysis-Transient%20Thermal-orange?style=for-the-badge" alt="Transient Thermal">
  <img src="https://img.shields.io/badge/Physics-Conduction%20%2B%20Convection-blue?style=for-the-badge" alt="Thermal Physics">
  <img src="https://img.shields.io/badge/Status-Research%20Study-success?style=for-the-badge" alt="Research Study">
</p>

> **A transient thermal investigation of heat propagation between cylindrical lithium-ion cells, structural-steel support plates, and mica thermal barriers using ANSYS Mechanical.**

---

## 🧭 Overview

This project investigates how heat generated in one lithium-ion battery cell propagates through a multi-cell battery assembly.

The model contains:

- 🔋 Multiple lithium-ion battery cells
- 🧱 Structural-steel support members at the top and bottom
- 🟨 Mica thermal-isolation barriers between selected cells
- 🌬️ Convective heat transfer from exposed surfaces
- 🔥 A locally heated battery cell
- ⏱️ Transient thermal analysis to observe temperature evolution with time

The central engineering question is:

> **Can a thin mica barrier reduce thermal propagation from a heated lithium-ion cell to its neighbouring cells?**

---

# 🖼️ Simulation & Model Visuals

The repository contains the five project images used to document the CAD model, ANSYS setup, transient thermal behaviour, and final temperature results.

### 1. CAD / Battery Assembly

![Full battery and structural enclosure](Full+Battery+with+Box.step)

> **CAD source:** `Full+Battery+with+Box.step`  
> The STEP file contains the complete battery assembly and enclosure/support geometry. GitHub cannot render STEP geometry directly in the README; download the file and open it in a CAD package such as Fusion 360, SolidWorks, FreeCAD, or another STEP-compatible viewer.

### 2. ANSYS Model / Setup

![ANSYS battery thermal model setup](<Screenshot 2026-09-08 163523.png>)

**ANSYS model/setup reference — `Screenshot 2026-08-19 082915.png`**

This image documents the ANSYS model and provides visual evidence of the simulation setup.

### 3. ANSYS Thermal Analysis

![ANSYS transient thermal analysis](<Screenshot 2026-08-19 082915.png>)

**Transient thermal analysis — `Screenshot 2026-09-08 163523.png`**

This image shows the thermal-analysis environment and the corresponding simulation/result information.

### 4. Transient Temperature Result

![Transient temperature result](<image (1).png>)

**Transient temperature behaviour — `image (1).png`**

This result is used to examine how temperature evolves through the battery assembly during the transient simulation.

### 5. Temperature Distribution / Contour

![Battery temperature distribution](<image (2).png>)

**Temperature distribution — `image (2).png`**

The temperature field illustrates the hot region surrounding the heated cell and the subsequent propagation of heat through neighbouring regions and structural components.

### 6. Additional Simulation View

![Additional ANSYS simulation result](<image.png>)

**Additional simulation/result view — `image.png`**

This image provides additional visual documentation of the numerical model and its thermal response.

> **Note:** The image filenames above intentionally match the filenames stored in this repository. Keeping the images in the repository root allows GitHub to render them directly inside this README.

---

# 🎯 Objectives

1. Model transient heat propagation through a battery assembly.
2. Study heat conduction through the structural-steel support.
3. Investigate the thermal-isolation effect of mica between cells.
4. Compare temperatures of neighbouring cells with and without mica separation.
5. Identify the dominant heat-transfer paths.
6. Establish a foundation for a more advanced battery thermal-management study.

---

# 🧩 Model Configuration

The CAD assembly is provided as:

**`Full+Battery+with+Box.step`**

The thermal model represents a battery pack in which the cells are mechanically supported by structural members.

### Main thermal paths

```text
                  STRUCTURAL STEEL
        ┌─────────────────────────────────┐
        │          ↓ CONDUCTION            │
        └─────────────────────────────────┘
                 │       │       │
              🔋 CELL  🔥  🔋 CELL
                    │
              MICA BARRIER
                    │
                 🔋 CELL
                    │
        ┌─────────────────────────────────┐
        │          ↑ CONDUCTION            │
        └─────────────────────────────────┘
                  STRUCTURAL STEEL
```

The heated cell acts as the primary thermal source.

---

# 🔥 Heat Generation

For an electrically operating battery, electrical power can be represented by:

\[
P = VI
\]

where:

- \(P\) = electrical power [W]
- \(V\) = cell voltage [V]
- \(I\) = current [A]

In a real lithium-ion cell, not all electrical power becomes heat. A physically complete battery thermal model can include:

- Ohmic/Joule heating
- Polarization heat
- Entropic heat
- Reaction heat
- Heat generation varying with SOC
- Heat generation varying with temperature
- Internal resistance varying with SOC and temperature

This project uses a simplified thermal representation intended to study **heat propagation and thermal isolation**, rather than a complete electrochemical battery model.

---

# 🌡️ Initial Condition

The initial temperature of the assembly is:

**22 °C**

The transient solution then tracks the temperature field as heat propagates through the battery structure.

---

# 🌬️ Convection

Convective heat transfer occurs from surfaces exposed to the surrounding environment.

The governing relationship is:

\[
q = hA(T_s-T_\infty)
\]

where:

| Parameter | Meaning |
|---|---|
| \(q\) | Heat-transfer rate [W] |
| \(h\) | Convective heat-transfer coefficient [W/m²·K] |
| \(A\) | Exposed surface area [m²] |
| \(T_s\) | Surface temperature [°C or K] |
| \(T_\infty\) | Ambient temperature [°C or K] |

### Important modelling point

The mica sheets do **not** simply "block conduction."

Mica is itself a solid material and can conduct heat.

In this configuration, the mica barriers mainly reduce the **directly exposed cell surface area available for convection** and introduce an additional solid thermal-resistance path where heat must pass through the mica.

Therefore:

```text
Without mica:

CELL → AIR
       ↓
   CONVECTION


With mica:

CELL → MICA → surrounding structure/environment
       ↓
 additional thermal resistance
```

The exact behaviour depends on the mica thickness, thermal conductivity, contact conditions, and exposed surfaces.

---

# 🟨 Mica Thermal Barrier

Mica is used as an electrically insulating and thermally resistant material in battery-related applications.

Its effectiveness depends strongly on:

\[
R_{mica} = \frac{L}{kA}
\]

where:

- \(R_{mica}\) = thermal resistance
- \(L\) = mica thickness
- \(k\) = mica thermal conductivity
- \(A\) = heat-transfer area

### Engineering interpretation

Increasing mica thickness generally increases the through-thickness thermal resistance:

\[
L \uparrow \Rightarrow R_{mica} \uparrow
\]

while increasing thermal conductivity decreases it:

\[
k \uparrow \Rightarrow R_{mica} \downarrow
\]

The exact material values used in ANSYS should be recorded in the Engineering Data section of the project.

---

# 🧱 Structural Steel Heat Path

The model contains structural steel at the **top and bottom of the battery cells**.

Steel has relatively high thermal conductivity compared with insulating materials.

Consequently, the steel creates a significant conductive pathway:

```text
             HEATED CELL
                  🔥
                 / \
                /   \
               ↓     ↓
        STRUCTURAL STEEL
               ↓     ↓
        neighbouring regions
```

This is an important observation from the simulation.

Although mica can reduce thermal propagation through selected cell-to-cell paths, the steel support can provide an alternative route for heat transport.

### This creates a key research question:

> **Is the apparent thermal isolation of the mica barrier still effective when the battery cells are connected through a highly conductive structural support?**

This is considerably more interesting than simply comparing "mica vs no mica."

---

# 📊 Simulation Results

The current simulation produces the following observed temperature behaviour.

### 🔥 Heated region

The highest reported temperature is approximately:

**69.779 °C**

### 🔋 Neighbouring cell without the same mica isolation

The neighbouring cell reaches approximately:

**34–40 °C**

### 🟨 Neighbouring cell separated by the mica barrier

The neighbouring cell remains around:

**28 °C**

### Initial condition

**22 °C**

---

# 📈 Key Observation

The temperature distribution demonstrates that the thermal barrier changes the rate and magnitude of thermal propagation.

A simplified comparison is:

| Region | Approx. temperature |
|---|---:|
| Initial assembly | **22 °C** |
| Mica-separated neighbouring cell | **~28 °C** |
| Other neighbouring cell(s) | **~34–40 °C** |
| Heated region / maximum | **~69.779 °C** |

These values are **numerical simulation results**, not experimental measurements.

The result suggests that the mica barrier can substantially reduce the temperature rise of a neighbouring cell under the simulated conditions.

---

# 🔬 Thermal Physics Interpretation

The battery assembly involves several simultaneous thermal mechanisms.

### 1. Conduction through solids

Fourier's law:

\[
\vec q=-k\nabla T
\]

Heat flows from regions of higher temperature toward regions of lower temperature.

---

### 2. Convection to the environment

\[
q=hA(T_s-T_\infty)
\]

The exposed surfaces lose heat to the surrounding air.

---

### 3. Thermal resistance of mica

\[
R=\frac{L}{kA}
\]

The mica layer adds resistance to heat transfer through the barrier.

---

### 4. Conductive bypass through steel

Even if a mica barrier reduces one heat path, heat can travel through the structural steel.

This is why thermal management must consider the **entire thermal network**, rather than a single material.

---

# 🧠 Thermal Network Concept

The assembly can be interpreted as a thermal-resistance network:

```text
                       ┌── Convection ──→ Ambient
                       │
🔥 Heated Cell ────────┼── Steel ───────→ Other cells
                       │
                       └── Mica ────────→ Other cells
```

The actual temperature of each cell is determined by the competition between:

- Heat generation
- Conduction
- Contact resistance
- Mica resistance
- Steel conduction
- Convection
- Thermal mass
- Transient time

---

# ⏱️ Why Transient Thermal Analysis?

A steady-state analysis answers:

> "What temperature does the system eventually reach?"

A transient analysis answers:

> **"How does the temperature change with time?"**

This is particularly important for batteries because thermal propagation is time-dependent.

The transient heat equation can be represented as:

\[
\rho c_p\frac{\partial T}{\partial t}
=
\nabla\cdot(k\nabla T)+\dot q
\]

where:

- \(\rho\) = density
- \(c_p\) = specific heat capacity
- \(k\) = thermal conductivity
- \(T\) = temperature
- \(t\) = time
- \(\dot q\) = volumetric heat-generation rate

---

# 🧪 What This Study Demonstrates

The simulation demonstrates a fundamental battery thermal-management principle:

> **Thermal isolation is not determined by one material alone. The complete geometry and all available conductive and convective heat paths must be considered.**

The mica barrier can reduce thermal propagation between selected cells, but structural components can create alternative conductive paths.

This makes the assembly-level thermal design important.

---

# 🔎 Research Opportunities

This model can be expanded into a much stronger engineering research project.

## 1. Mica thickness study

Run:

- 0 mm
- 0.5 mm
- 1 mm
- 1.5 mm
- 2 mm
- 3 mm

Compare neighbouring-cell temperature.

---

## 2. Material comparison

Compare the existing structural steel with alternatives such as:

- Aluminium
- Stainless steel
- Polymer composites
- Glass-fibre reinforced polymer
- Carbon-fibre composite
- Engineering plastics

The objective would be to determine whether mechanical requirements can be maintained while reducing unwanted thermal conduction.

---

## 3. Mica vs no mica

Create two cases:

**Case A:** No thermal barrier

**Case B:** Mica barrier

Compare:

\[
\Delta T_{neighbor}
=
T_{neighbor}-T_{initial}
\]

---

## 4. Different convection coefficients

Perform a sensitivity study using different \(h\) values representing different cooling conditions.

This can show whether the effectiveness of the mica barrier changes under:

- Natural convection
- Weak forced convection
- Strong forced convection

---

## 5. Heat-generation sensitivity

Repeat the analysis for different battery heat-generation rates.

This is especially important because real battery heat generation changes with current.

---

## 6. Thermal runaway propagation study

A more advanced extension would model a much more severe thermal event.

Possible future work:

```text
Cell 1 heating
     ↓
Cell 2 temperature rise
     ↓
Cell 3 temperature rise
     ↓
Thermal propagation risk
```

This would move the project toward **battery safety and thermal-propagation research**.

---

# 📐 Suggested Performance Metrics

Future simulations should report:

### Maximum temperature

\[
T_{max}
\]

### Temperature rise

\[
\Delta T=T-T_0
\]

### Thermal propagation delay

Time required for a neighbouring cell to reach a specified temperature.

### Temperature difference

\[
\Delta T_{cell}=T_{hot}-T_{neighbor}
\]

### Heat flux

\[
q''=-k\nabla T
\]

### Thermal resistance

\[
R_{th}=\frac{\Delta T}{Q}
\]

These metrics make the work easier to compare scientifically.

---

# ⚠️ Model Limitations

This study should **not** be interpreted as a complete electrochemical battery model.

Current limitations include:

- Simplified heat-generation representation
- No detailed electrochemical reaction model
- No SOC-dependent heat generation
- No temperature-dependent internal resistance unless explicitly implemented
- Simplified convection boundary conditions
- Material properties may be treated as constant
- Contact thermal resistance may be simplified
- No experimental validation yet
- Thermal runaway chemistry is not explicitly modelled

These limitations are not weaknesses of the project; they define the scope of the current study and provide clear directions for future work.

---

# 📁 Repository Contents

| File | Type | Purpose |
|---|---|---|
| `Full+Battery+with+Box.step` | CAD | Complete battery assembly / enclosure geometry |
| `Screenshot 2026-08-19 082915.png` | Image | ANSYS model/setup reference |
| `Screenshot 2026-09-08 163523.png` | Image | ANSYS transient thermal analysis reference |
| `image (1).png` | Image | Transient temperature/result documentation |
| `image (2).png` | Image | Temperature distribution / contour |
| `image.png` | Image | Additional simulation/result view |

---

# 🛠️ Software

- **ANSYS Mechanical 2025 R1**
- ANSYS Engineering Data
- ANSYS Transient Thermal
- CAD STEP geometry
- Finite Element Method (FEM)

---

# 🚀 Future Version

The next version of this study can evolve into:

### **Battery Thermal Management Optimization**

with automated parametric simulations:

```text
Material
   ↓
Mica thickness
   ↓
Heat generation
   ↓
Convection coefficient
   ↓
Transient simulation
   ↓
Tmax / ΔT / heat flux
   ↓
Optimization
```

The final objective would be to identify a configuration that provides:

**Low cell temperature + low cell-to-cell thermal propagation + adequate mechanical support.**

---

# 📚 Scientific Takeaway

The most important finding from the current model is that **thermal isolation must be evaluated at the assembly level**.

A mica barrier may reduce direct thermal interaction between cells, but a conductive structural component can provide a parallel heat-transfer path.

Therefore, the thermal design problem is not simply:

> **"Is mica a good insulator?"**

It is:

> **"How does the complete combination of cell geometry, mica barriers, structural material, contact interfaces, heat generation, and convection determine thermal propagation through the battery pack?"**

That is the question this simulation provides a foundation to investigate.

---

## 👤 Author

**Zayannnnn**

Mechanical Engineering Student  
Battery Thermal Management & CAE Study

---

## ⭐ Project Status

**Current stage:** Transient thermal simulation completed  
**Primary focus:** Thermal propagation and mica isolation  
**Next stage:** Parametric optimization + experimental/analytical validation

> ⚠️ **Research note:** Simulation results are dependent on geometry, mesh quality, material properties, boundary conditions, and heat-generation assumptions. Results should be validated experimentally before being used for safety-critical battery design.
