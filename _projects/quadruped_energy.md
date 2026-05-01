---
title: Parameterizable Quadruped Energy Analysis
skills: 
  - Gazebo
  - ROS2
  - C++
  - Python
repo: nathanwolfsonkin/quadruped
---
##### This work was presented at the ASME International Mechanical Engineering Congress and Exposition 2025.

This project investigates how early-stage mechanical design decisions influence energy efficiency in quadrupedal robots. The study introduces two complementary modeling approaches: a kinematic model that estimates energy expenditure from motion alone, and a dynamic model that incorporates joint torques and contact dynamics for higher-fidelity analysis. While the models did not accuratley compute cost of transport, they did meaningfully capture trends in the variation in cost of transport with respect to mass. This was validated against trends seen in nature.

{% include figure.html 
   image="/images/research/body_mass_variations.png"
   width="100%"
%}

For full context, please read [the paper](https://doi.org/hbztb5)!