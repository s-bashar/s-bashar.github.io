---
layout: post
title: Baby Pacifier Sensor
description: Embedded a pressure/vacuum sensor into pacifiers to replace the subjective "gloved finger" test, providing clinicians with quantitative data for diagnosing newborn feeding issues during a critical window.
skills: 
  - Sensor Testing and Data Analysis (VNA Testing + Python Scripting) 
  - Flex PCB Design (Altium) 
  - CAD (Fusion360/OnShape)
  - Transmission Line Design (Ansys HFSS)
  - Sensor Fabrication 
 
main-image: /overview_9.png
---

# Awards:
Best Poster Award in ECE at UC San Diego’s Research Expo 2025

# Poster:
{% include image-gallery.html images="PaciForce_Poster_vertical.png" height="1800" alt="Poster" %}


# Contributions: 

### Improved Fabrication of Sensor

- **Enhanced performance and manufacturability**:
  - Increased sensor batch yield by **80%** by improving polymer adhesion techniques and eliminating air bubbles
  - Improved sensor consistency by **reducing operating frequency standard deviation by 80%** through optimized polymer-based geometry
  - Reduced fabrication time by **25%** by streamlining processes and eliminating redundant steps
  - Increased sensitivity by **167%** by selecting and optimizing polymer material composition

- **Testing and validation**:
  - Conducted **vacuum pressure performance testing** to benchmark the sensor against industry-standard pacifier sensors  
    → Validated dual-functionality for both force and vacuum pressure sensing
  - Performed **sensor testing and data analysis** across multiple batches to identify fabrication improvements affecting yield, consistency, and sensitivity

- **Automation and data processing tools**:
  - Developed a **MATLAB script** to:
    - Communicate with a VNA, Arduino, and linear actuator
    - Apply step forces and collect **S11 parameter data**
    - Generate **phase vs. force** graphs for performance analysis
  - Created an algorithm to:
    - Automatically identify the **optimal operating frequency** (maximizing phase change)
    - Ensure linearity and control for differential magnitude > −5 dB




 

