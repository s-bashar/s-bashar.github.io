---
layout: post
title: Custom 8-bit Adder 
description: Course Project for advancded digital design @UC San Diego (ECE165 Professor Patrick Mercier), goal of this project was to show that a custom 8-bit adder could out perform an automatic place and route(APR) ripple carry adder given a designer is familiar with the basic concepts of VLSI.
skills: 
  - Cadence Virtuoso
  - transisent simulations
  - frequency optimizing 
  - Combinational and Sequential Logic design
 

main-image: /full_adder_pic.png
---

# Design choice 

To overcome the limitations of the RCA, CLA, and CSA, the parallel prefix adder (PPA) architecture has emerged as a promising solution. The PPA architecture addresses the challenge of carry propagation delays by utilizing a tree-like structure with multiple levels of carry computations. By leveraging parallel processing of carry signals, the PPA significantly reduces the critical path delay and enhances overall speed performance. This innovative architecture enables efficient carry signal propagation through various paths, allowing for faster addition of multi-bit numbers. The PPA offers improved performance and reduced latency compared to traditional adder architectures, making it an attractive choice for high-speed arithmetic operations. 
Two noteworthy variations of traditional PPA architecture include the Brent-Kung adder and the Kogge-Stone adder. The Brent-Kung adder offers improved power efficiency because of its lowest area delay with large number of input bits. However, the large number of levels in this architecture reduces its operational speed [7]. The Kogge-Stone adder has minimal fan-out and logic depth. Thus, the Kogge-Stone adder architecture becomes one of the fastest adders that is favored in electronic technology. However, as a tradeoff the KSA has a larger area



