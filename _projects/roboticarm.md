---
title: Optimal Control of a 3-Link Robotic Arm
skills: 
  - MATLAB
repo: nathanwolfsonkin/Three-Link-Arm
---

{% include two_images.html 
   src1="/images/personal/roboticarm/OptimalAnimation.gif"
   src2="/images/personal/roboticarm/FeedbackAnimation.gif" 
   width1="48%"
   width2="48%"
   gap="1rem"
%}

{% include section.html %}

This project was an exercise in understanding optimal control application on a non-linear system. The Linear Quadratic Regulator (LQR) controller was able to achieve superior tracking and less energy usage than a baseline proportional controller. The LQR controller used both feed forward and feedback while the proportaional controller used only positional feedback.

Since LQR is a linear controller and the three link robotic arm is a highly nonlinear system, the dynamics of the arm were linearized in advance about every point along the prescribed trajectory. This ensured that the LQR controller was implementable without needing to linearize about every possible point in the reachable state space.
