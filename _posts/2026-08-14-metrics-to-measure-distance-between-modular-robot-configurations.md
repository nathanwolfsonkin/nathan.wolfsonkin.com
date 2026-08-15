---
title: Metrics to Measure Distance Between Modular Robot Configurations
tags:
- modular-robotics
- metrology
- graph-theory
---


A bit of a shorter post this week since I've been a bit busy with non-academic work this week.


In the pursuit of defining reconfigurability of modular robots, it may be desirable to measure how different two configurations are. In that spirit, I have spent this week reading about metrics to measure the configuration space distance between modular robots. First it's important to define what properties a distance function must have. A distance function is defined by the following properties [1]:


$$d(A,B) \geq 0 ~~ \text{and} ~~ d(A,B) = 0 \iff A = B$$


$$d(A,B) = d(B,A)$$


$$d(A,B) + d(B,C) \geq d(A,C)$$


The simplest possible distance function which has these properties is the discrete metric


$$\delta^{(0)} = \begin{cases} 1 & A \neq B \\ 0 & A=B \end{cases}$$


[1] defined a number of metrics based on distances in configuration space for planar hexagonal MRRs. A metric which defines module overlap was defined based on the following:


$$\delta^{(1)}(A,B)=n- \left\| A \cap B \right\|$$


In a planar environment it is quite clear how an overlap is measured. This makes me curious if graph overlap is a well studied idea. Measuring how much two unlabeled graphs overlap could be an important tool for transferring these planar, hexagonal ideas to a more generic graph based approach.


Another metric counts the minimal number of valid reconfiguration moves required to reconfigure from one configuration to another. This is similar to the reconfiguration example from last week's post.


$$\delta^{(2)}(A,B)=M_{min}(A,B)$$


Separately I have been reading about non-isomorphic graph enumerations. I figured that if the number of non-isomorphic graphs could be enumerated under a given set of constraints, that would make the total number of possible configurations in configuration space much more easily measurable. The problem is that [2] only enumerates the number of isomorphic trees that can be generated. This can still be useful, but if we want to find all possible chain configurations.

## Citations

[1] A. Pamecha, I. Ebert-Uphoff, and G. S. Chirikjian, “Useful metrics for modular robot motion planning,” IEEE Trans. Robot. Automat., vol. 13, no. 4, pp. 531–545, Aug. 1997, doi: 10.1109/70.611311.

[2] “Enumerating the Non-Isomorphic Assembly Configurations of Modular Robotic Systems”.
