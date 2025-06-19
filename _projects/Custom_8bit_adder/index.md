---
layout: post
title: Custom 8-bit Adder 
description: Course Project for advancded digital design @UC San Diego (ECE165 Professor Patrick Mercier), goal of this project was to show that a custom 8-bit adder could out perform an automatic place and route(APR) ripple carry adder given a designer is familiar with the basic concepts of VLSI.
skills: 
  - Cadence Virtuoso
  - transisent simulations
  - frequency optimizing 
  - Combinational and Sequential Logic design
  - Dynamic Loigc + Skewed Inverters + Dominio Logic
 

main-image: /full_adder_pic.png
---

# Design choice 

To overcome the limitations of the RCA, CLA, and CSA, the parallel prefix adder (PPA) architecture has emerged as a promising solution. The PPA architecture addresses the challenge of carry propagation delays by utilizing a tree-like structure with multiple levels of carry computations. By leveraging parallel processing of carry signals, the PPA significantly reduces the critical path delay and enhances overall speed performance. This innovative architecture enables efficient carry signal propagation through various paths, allowing for faster addition of multi-bit numbers. The PPA offers improved performance and reduced latency compared to traditional adder architectures, making it an attractive choice for high-speed arithmetic operations. 
Two noteworthy variations of traditional PPA architecture include the Brent-Kung adder and the Kogge-Stone adder. The Brent-Kung adder offers improved power efficiency because of its lowest area delay with large number of input bits. However, the large number of levels in this architecture reduces its operational speed [7]. The Kogge-Stone adder has minimal fan-out and logic depth. Thus, the Kogge-Stone adder architecture becomes one of the fastest adders that is favored in electronic technology. However, as a tradeoff the KSA has a larger area.

We choose to use dynamic logic over static complementary CMOS and other techniques since it offers us the chance to use less transistors, it requires N+2 transistors while static CMOS uses 2N and pseudo-NMOS uses N+1. Additional benefits compared are the smaller load capacitance, no static power, non-ratioed logic, it is also much faster since tpLH = 0 and tpHL is small and in pre-charge time is small. In general, about 1.3-2x faster than static CMOS. However, the downsides are high power consumption as well as noise leakage, charge sharing and inputs not being able to go from 1-0. We can still combat some of the issues by using a keeper transistor, extra pre-charge transistor and domino logic which we will get into. This influenced our design choice since we knew that we wanted to optimize for speed.

---

# Adder Blocks

## Propagate-Generate Cell:

The Propagate-Generate Cell (PG Cell) is a crucial component among the three distinct cells employed in the construction of our 8-bit Kogge-Stone adder. This cell serves as a pre-processing stage, responsible for computing generate and propagate signals for each pair of input bits, denoted as A and B. The generation of these signals follows a well-defined logic, governed by the following equations:
<br>
pi = Ai ⊕ Bi
<br>
gi = Ai . Bi

{% include image-gallery.html images="PG_Cell.png" height="400" alt="PG_cell" %}

## Fundamental Carry Operator 

The Fundamental Carry Operator Cell (FCO Cell) serves as the second key component within our 8-bit Kogge-Stone adder. It can be conceptualized as a block comprising a group propagate and generate structure, or as a carry look-ahead network. These intermediate signals, denoted as group propagate and generate, play a pivotal role in the adder’s operation, and are determined by the following logic equations:
<br>
Pi:j = Pi:k+1 . Pk:j
<br>
Gi:j = Gi:k+1 ∨ (Pi:k+1 . Gk:j)

{% include image-gallery.html images="FCO_CELL.png" height="400" alt="FCO_Cell" %}

## Post Processing Carry Cell:

The Post Processing Carry cell (PPC Cell) is one halve of the third and final distinct cell to complete the construction of our 8-bit Kogge-Stone adder. This cell serves as a part of the post-processing stage, responsible for the carry out values given the P and G values from the prior FCO stage as well as the carry in. The signals can be illustrated with the following logic equation:
<br>
Ci = (Pi . Cin) ∨  Gi

{% include image-gallery.html images="PPC.png" height="400" alt="PPC_cell" %}

## Post Processing Sum Cell:

The Post Processing Sum Cell (PPS Cell) is the second halve of the third and final distinct cell to complete the construction of our 8-bit Kogge-Stone adder. This cell serves as a part of the post-processing stage, responsible for the output of the sum values. The signals can be illustrated with the following logic equation:
<br>
Sumi = pi ⊕ Ci-1

{% include image-gallery.html images="PPS.png" height="400" alt="PPS_Cell" %}

---

# OR + AND transistor level implementation with dynamic & domino logic + high skew inverter

## AND Gate:

{% include image-gallery.html images="AND.png" height="400" alt="AND_Cell" %}

Shows the transistor level implementation of the AND gate found in the PG, PPC and FCO cell. This gate is utilizing dynamic and domino logic, giving way to faster operation. We have placed a high-skew inverter at the output of the AND gate to favor a rising edge transition to be able to take advantage of the lower logical effort needed for the gate.

## OR Gate:

{% include image-gallery.html images="OR.png" height="400" alt="OR_Cell" %}

Shows the transistor level schematic of the OR gate utilizing dynamic and domino logic to provide lower logical effort and therefore faster operation. The OR gate is found in multiple cells that are crucial for the operation of the 8-bit adder such as the PPC and FCO cell. This custom designed gate also utilizes a high skew inverter, favoring a critical rising edge on the output, and using less logical effort compared to an un-skewed inverter.

# Transisent simulation and Results

## Automatic place and route ripple carry adder vs. Kogge-Stone Adder

{% include image-gallery.html images="pnr.png" height="400" alt="PNR trans sims" %}
##### Automatic Place and Route Adder simulation at fMax=2.2Ghz
{% include image-gallery.html images="KSA.png" height="400" alt="PNR trans sims" %}
##### Kogge-Stone Adder at fMax=3Ghz

## Table Results:

|    	| Header 2 | Header 1 | 
|--------------------------|
|		|Performance for VDD= 1.1V |
| fMax |Row 1, Col 1 | Row 1, Col 2 |
| Power consumption @ fmax|Row 2, Col 1 | Row 2, Col 2 |


## Suggestions for futre Iterations:

