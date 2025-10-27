---
layout: post
title: 'Project One'
---
I am currently working on developing a custom dashboard for the student built race car I work on for my project team at Cornell.

Present: Writing a custom library to directly access coprocessor graphics commands through register manipulation in the coprocessor RAM

10/25/25: Tested on board CAN bus technology, created a custom harness and successfully sent and recieved data over CAN.

<img src="/assets/img/projects/proj-1/IMG_0583.jpg" alt="CAN Bus Testing" width="400">


10/24/25: Completely continuity tested board, found and corrected physical errors in board (shorted terminals and faulty components)

10/22/25: Brought up board using solder oven and hand soldering




Over the summer I conducted R&D to select parts and develop a plan for my board ([Summer Design Report](https://docs.google.com/document/d/1WKc7Q3VKmvlFOh2o1Y_aCp5rCdYjmxY-hWMD89qIQBE/edit?usp=sharing)). In early September, I completed a layout of my board on Altium. The board went through design review and I made slight changes ([Preliminary Design Report](https://docs.google.com/document/d/1wmj2EkKXVpfNvsFNHgp13AmDA0lCqhSfUNw64zUEh54/edit?usp=sharing)), until I ordered and brought up the board in early October. I utilized I mostly recently tested my on board CAN line, successfully sending and recieving data. I am currently developing a firmware suite to write directly to the onboard RAM of my screen driver module to allow me to execute advanced visual functions, display images, and display animations. 

<div style="display:flex; justify-content:center; gap:10px; flex-wrap:wrap;">
  <img src="/assets/img/projects/proj-1/schematic3D.png" alt="3D Board Schematic" style="width:45%; border-radius:10px;">
  <img src="/assets/img/projects/proj-1/schematic2D.png" alt="2D Board Schematic" style="width:45%; border-radius:10px;">
</div>
