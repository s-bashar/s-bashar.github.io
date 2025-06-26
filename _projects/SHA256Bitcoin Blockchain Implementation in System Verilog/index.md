---
layout: post
title: SHA256+Bitcoin Hashing RTL Model System Verilog Implementation
description: We implemented RTL models of the SHA-256 and Bitcoin hashing algorithms in SystemVerilog as part of a exploration into hardware design trade-offs. The goal was to compare serial and parallel implementations and understand how design choices impact key metrics like area, cycle count, and maximum operating frequency (fmax). By optimizing for each of these variables individually, we observed how improvements in one metric often came at the cost of others. This allowed us to gain insight into real-world architectural trade-offs in ASIC/FPGA design and how they apply to compute-intensive workloads like cryptographic hashing. (ECE111, Advanced Digital Design Course Project, @UC San Diego Prof. Farinaz Koushanfar) 
  - Intel Quartus Prime
  - System Verilog 
  - Cryptographic Hash Function
  - Parallel Computing 
 

main-image: /overview.png
---

# SHA-256 Properties:

{% include image-gallery.html images="sha256_prop.PNG" height="400" alt="sha256_properties" %}
   
  - Compression: Given a variable input size, outputs a fixed length
  - Avalanche Effect: A small change in input, even a single character, creates a significant change to the output
  - Determinism: The same input will give the same output
  - One-Way: No way to reverse engineer the output back to the input, inshuring security
  - Collision Resistance: Two distinct inputs have low probability to have the same output 
  - Efficient: SHA-256 balances security and speed.
  - w