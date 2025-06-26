---
layout: post
title: Force Sticker 
description:  
    We show that the force-information can be piggybacked over existing RFIDs, with no additional power and requirement of any interfacing electronics, by simply interfacing a force sensitive capacitor to the RFID. Hence, the designed force-stickers consist of a thin parallel-plate capacitor, smaller than a rice grain that deforms under applied force, and is interfaced in between the RFID squiggly antenna and the RFID IC. But, how does the force-information from the capacitor get communicated via the RFID IC, without requiring any more electronics and power? The secret sauce lies in the capacitor-design, choosing the correct polymer and correct dimensions! 
skills: 
  - Rigid/Flex PCB Design (Altium Designer)
  - DFT
  - Antenna/PCB Simulations (Ansys HFSS)
  - Low-Power Systems 
  - RF Transmission Lines
  - Small Antenna Design

main-image: /force-sticker-banner_8.png
---

---

# Design of ForceSticker:

WiForceStickercreates a new class of sticker-like force sensors which are capable of wireless readout without battery, to serve in-vivo and ubiquitous 
weight sensing applications. This is enabled by piggybacking analog sensor data onto a digitally identified RFID link. 

{% include image-gallery.html images="design2.png" height="400" alt="Design2" %}
{% include image-gallery.html images="design2.png" height="400" alt="Design2" %}
##### When a capacitor is interfaced to an antenna, it shows a non-linear relationship between the frequency, capacitance and the phase change. We find that when capacitor is designed between 1–10 pF range, the phase change effect is sensitive to RFID frequency of 900 MHz

{% include image-gallery.html images="design.png" height="400" alt="Design" %}

##### Shows ForceSticker components, b.i, ii) Shows capacitor sensor compared to a rice grain, zoomed in view c) Shows how the capacitor sensor is attached to the RFID IC (peeled off in the image via tweezers) via hair-like tungsten filaments highlighted in red, can be seen more clearly in a) and b.ii)

---
# Experiments with ForceStickers: 

## Package Consistency checks with ForceStickers:
{% include image-gallery.html images="experiment1.png" height="400" alt="Experiment 1" %}

##### We show that by sticking ForceStickers to bottom of packages, we can sense weight and determine number of items kept inside, for consistency checks in warehouse settings. We take 160 measurements with different number of items (RPis placed in the package) and obtain classification confusion matrix.

---
## Sensing knee-impact forces:
{% include image-gallery.html images="experiment2.png" height="400" alt="Experiment 2" %}

##### We show how ForceSticker can be prototyped with a custom Flexible PCB RFID, that allows us to make a 2x smaller ForceSticker, and makes it small enough to allow sensing forces from a knee-joint

This showed that ForceSticker can even be used in scenarios like knee-implants which are irregularly shaped and massively space constraint. Further, by monitoring the knee joint forces over time, the implant’s fit and function can be evaluated, as well as the implant health, if the implant starts wearing down then the sensed force will also change.

---

## Cyclic testing of ForceSticker:

Robustness test of the sensor by applying forces on it using an in-house developed automated actuator-based cyclic test setup

{% include image-gallery.html images="experiment3.png" height="400" alt="Experiment 3" %}

##### The cyclical testing setup where an actuator applies forces on the sensor, and we see that even after 10,000 force presses by the actuator, the sensor’s error performance remains about the same (0.3N)

---
# Quick Video Summary:

{% include youtube-video.html id="arSO7shzFT4" autoplay= "false"%}
---
# Future Work

Even though the sensors we designed were thin sticker-like, enabled first demonstrations of bunch of interesting applications and even turned out to be robust, ForceSticker is still research in motion and there is a lot of ground to cover before we could achieve the force vision showed earlier.

The biggest roadblock lies in enabling such ForceStickers to work with smartphones, since the existing ForceStickers only work with dedicated RFID readers, which may not be always available. Further, we need to realize mass fabrication of these sensors (right now it is mostly manual and DIY assembly), explore commercially-viable materials for everyday life applications, and bio-degradable hermetically sealed sensors for in-vivo applications. We also need to improve the error performance of the sensor in more challenging environments, and scaling the performance to a large number of sensors.

# References:
[1] “ForceSticker: Wireless, Batteryless, Thin & Flexible Force Sensors”, Gupta el al. IMWUT Issue 1 2023 <br>
[2] “WiForce: Wireless Sensing and Localization of Contact Forces on a Space Continuum”, Gupta et al. NSDI’21 <br>
[3] “Soft Radio-Frequency Identification Sensors: Wireless Long-Range Strain Sensors Using Radio-Frequency Identification”, Teng at al. SORO’19 <br>
[4] “MARS: Nano-Power Battery-free Wireless Interfaces for Touch, Swipe and Speech Input”, Arora et al UIST’21 <br>
