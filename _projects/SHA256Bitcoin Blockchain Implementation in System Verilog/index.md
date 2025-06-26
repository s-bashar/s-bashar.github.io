---
layout: post
title: SHA256+Bitcoin Hashing RTL Model System Verilog Implementation 
description:  
    We implemented RTL models of the SHA-256 and Bitcoin hashing algorithms in SystemVerilog as part of a exploration into hardware design trade-offs. The goal was to compare serial and parallel implementations and understand how design choices impact key metrics like area, cycle count, and maximum operating frequency (fmax). By optimizing for each of these variables individually, we observed how improvements in one metric often came at the cost of others. This allowed us to gain insight into real-world architectural trade-offs in ASIC/FPGA design and how they apply to compute-intensive workloads like cryptographic hashing. (ECE111, Advanced Digital Design Course Project, @UC San Diego Prof. Farinaz Koushanfar) 
skills: 
  - Intel Quartus Prime
  - System Verilog
  - Parallel Computing 

main-image: /overview.png
---

---

# SHA-256 Properties:

{% include image-gallery.html images="sha256prop.png" height="400" alt="sha256_properties" %}