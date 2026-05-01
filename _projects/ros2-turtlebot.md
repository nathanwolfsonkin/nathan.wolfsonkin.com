---
title: ROS2 Navigation and Mapping
skills: 
  - ROS2
  - Python
repo: nathanwolfsonkin/ros2-turtlebot
---

{% include two_images.html 
   src1="/images/personal/ros2-turtlebot/robot_video.gif"
   src2="/images/personal/ros2-turtlebot/mapping_video.gif" 
   width1="45%"
   width2="45%"
   gap="3rem"
%}

{% include section.html %}

This project marked my first experience working with ROS2. The GIF on the left demonstrates the robot performing wall-following behavior, while the one on the right visualizes the mapping of the surrounding environment.

Infrared intensity readings were used as a proxy for estimating distance to nearby walls, enabling the wall_follow node to navigate effectively. At the same time, two services facilitated communication between the mapping and wall-following nodes: one allowed the wall_follow node to request the mapping node to record a new point, while the other enabled the mapping node to signal when mapping was complete, indicating that the robot could stop moving.

The mapping process was based on odometry data.

{% include centered_image.html 
   src="/images/personal/ros2-turtlebot/ROS2_flowdiagram.png" 
   width="100%" %}
