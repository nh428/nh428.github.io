---
layout: post
title: 'FPGA Bird Watcher'
---

My most recent project, I am working on developing an embedded system capable of identifying, tracking, and tagging birds. I am using the Radiona ULX3S FPGA board connected to an Ovo7670 camera module. Using [Angelo Jacobo's github project](https://github.com/AngeloJacobo/FPGA_RealTime_and_Static_Sobel_Edge_Detection), I am processing this camera data and performing a sobel edge detection algorithm on it. The aim of edge detection is to have accuracy identifying birds against a solid color sky background. I am currently repiping the interface of camera output from HDMI to a 40 pin 2.1" TFT screen for a more enclosed module. Future steps are writing the bird detection algorithm, which I plan to do by scanning for small, quick moving edges in frame. I then hope to attach the module to 2 servos, allowing for the camera to automatically try to position the bird in the middle of the frame. Finally, I hope to store camera data and port it to the on board SD card, allowing for video capture of the bird. 

This project was inspired by my current internship mentor and my grandfather, an avid ornithophile.
