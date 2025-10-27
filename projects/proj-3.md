---
layout: post
title: 'Project Three'
---

Processor was designed as a part of coursework for ECE 4750, Computer Architecture. This processor is a fully functional 5 stage pipelined processor with forwarding, hazard detection and stall logic, and an iterative multipler. The processor was first implemented and tested without forwarding logic, then reevaluated with forwarding to assess the total throughput gain. The 5 staged microprocessor was built from the ground up using completely synthesizable System Verilog code, utilizing fundamental logic blocks such as registers, muxes, and a regfile. A datapath-control unit design was implemented, with a FSM controlling logic signals to determine the route of data through the datapath depending on what instruction was recieved from memory. More information about this processor and its functionality can be found in my [lab report](https://www.overleaf.com/read/zfrfprnvpjzb#fe1304).

Below is a diagram of the microprocessor datapath with forwarding implemented.
<img src="/assets/img/projects/proj-3/ProcessorForwarding.png" alt="Microprocessor Datapath with Forwarding" width="400">

The iterative multipler of the lab was implemented in Verilog as well. It uses a shift and add variable latency approach with 0 chunking optimizations to reduce average cycles. Below is a diagram of the data path.
<img src="/assets/img/projects/proj-/iterativeMul.png" alt="Iterative Multiplier Diagram" width="400">

