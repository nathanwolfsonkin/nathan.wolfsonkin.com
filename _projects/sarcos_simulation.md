---
title: Sarcos Sapien 6M Digital Twin
skills: 
  - Gazebo
  - ROS2
  - Python
---

During my Summer 2024 internship at [JLG Industries](https://www.jlg.com){:target="_blank"}, I developed a digital twin of the Sarcos Sapien 6M robotic manipulator to support simulation, algorithm development, and real-world deployment. Using access to the system’s CAD models, I derived the kinematic frame relationships between the manipulator’s rigid bodies and constructed the robot model using Denavit–Hartenberg conventions.

The project had two primary objectives: first, to create a high-fidelity simulation environment for testing robotic algorithms, and second, to validate those algorithms on the physical robot. The initial application focused on autonomous tool-changing operations. Over the course of a 10-week internship, I designed and implemented both analytical and numerical inverse kinematics controllers, integrating them into the simulation and deployment pipeline.

The developed algorithms were successfully tested on a physical Sarcos Sapien 6M platform, where the robot completed tool-change operations that had first been validated in simulation. This work represented an early technical milestone in the broader robotics initiative at [JLG Industries](https://www.jlg.com){:target="_blank"}. My work on this project was an early step towards the [Oshkosh JLG Boom Lift with Robotic End Effector](https://www.ces.tech/ces-innovation-awards/2026/oshkosh-jlg-boom-lift-with-robotic-end-effector){:target="_blank"} project, which later received a 2026 CES Innovation Award.


{% capture left %}
{% include video.html src="/images/jlg/gazebo_tool_change.mp4" width="100%" %}
{% endcapture %}

{% capture right %}
{% include video.html src="/images/jlg/cropped_live_video.MOV" width="60%" %}
{% endcapture %}

{% include cols.html
   col1=left
   col2=right
%}
