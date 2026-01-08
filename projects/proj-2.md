---
layout: post
title: 'RSC-V Multi-core Processor'
---

This processor was designed as a part of coursework for ECE 4750, Computer Architecture. [lab report](https://www.overleaf.com/read/vhjkdttttvtz#0044bd) can be found here. The processor was first designed to be a fully functional 5 stage pipelined microprocessor with forwarding, a data and instruction cache, hazard detection and stalling logic, and an iterative multipler ([Report for microprocessor](https://www.overleaf.com/read/zfrfprnvpjzb#fe1304)). 4 instances of these microprocessors were then adapted and connected using a ring network topology to create a multi-core system. Further optimizations were made to increase processor performance, including fair router abritation, cache single cycle parallel read hits, a branch target buffer, and optimized sorting algorthim code. 
<div style="display:flex; justify-content:center; gap:10px; flex-wrap:wrap;">
  <img src="/assets/img/projects/proj-3/singleandmulti.png" alt="Single and Multicore Diagram" style="width:65%; border-radius:10px;">
</div>
<div style="display:flex; justify-content:center; gap:10px; flex-wrap:wrap;">
  <img src="/assets/img/projects/proj-3/ring.png" alt="Ring Network Topology" style="width:85%; border-radius:10px;">
</div>

Router distance and round robin arbitration tatics were used to optimize the network. A puesdo parallel cache was designed in order to optimize the common read hit case for a single cycle. We performed the tag check of our cache while bypassing the data at that specific address, then used control signals to confirm its validity in a single cycle. 
<img src="/assets/img/projects/proj-3/Cache.png" alt="Banked Cache Datapath Diagram" width="1000">
We also incorporated an F stage branch target buffer, decreasing the numnber of flushed instructions. We exploited temporal locality for each static branch instance in our program, storing its history up to 4 entries. We then used a branch table to predict the branch resolution while still in the F stage (Branches are resolved in the X stage of our processor, which has stages F D X M W). Finally, we performed optimizations on our benchmark, a sorting algortihm. After testing, Quicksort was selected for its high level of parallelism when translated to assembly. An optimized quicksort was developed in C that used insertion sort on small subsets of the array to reduce recursive stack function call overhead on small arrays.

The entirety of the datapath and control logic was coded using Synthesizeable Verilog in VSCode, using fundamental logic blocks such as registers, muxes, and regfiles. The implementation was built from the ground up, with a FSM controlling logic signals to determine the route of data through the datapath depending on what instruction was recieved from memory. A compiler was used to store the assembly instructions of our sorting algorthim in processor memory. A basic test suite was provided, however it was our responsibility to develop an extensive testing suite to be confident in the functionality of our processor. More information about this processor can be found in my [lab report](https://www.overleaf.com/read/vhjkdttttvtz#0044bd).

<img src="/assets/img/projects/proj-3/ProcessorForwarding.png" alt="Microprocessor Datapath" width="1000">

