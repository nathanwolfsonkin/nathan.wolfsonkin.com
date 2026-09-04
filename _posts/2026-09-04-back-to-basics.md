---
title: Back to Basics
tags:
   - modular-robotics
---


Research tends to be a long and meandering process. Oftentimes I will start with a heavily directed idea. This idea will lead me to look into another topic, which leads to the next topic, and before I know it, I end up looking into things that are seemingly unrelated to what I was originally trying to investigate. It is for this reason that I like to occasionally retrace my thinking to straighten out my meandering thoughts.


## The Basic Idea


This project started with a simple problem: modular reconfigurable robotic systems (MRRs) lack a standardized way to compare systems. Modern survey papers compare systems qualitatively [1, 2] rather than quantitatively. Qualitative measures are used because quantitative measures do not exist. One might assume that in a field dedicated to creating **modular** **reconfigurable** robots, someone might have figured out how to measure modularity or reconfigurability, but that doesn't appear to be the case.


Part of the reason for this lack of quantitative measure is that it is difficult to compare dissimilar systems. Someone asking the question "which system is more reconfigurable, Polypod or SMORES?" may as well be asking "which is greater, three meters or five newtons?" The question is unanswerable because in order to make comparisons, the comparators must be expressed in similar terms. Therefore the first step towards metric generation for MRRs must be to find the proper level of abstraction such that any two MRRs can be expressed in similar terms.


### A Unified Representation


A common representation for MRR configurations in the literature is the graph [3-8]. In this representation it is common for modules and their connections to be represented as vertices and edges respectively. To the best of my knowledge all MRRs can be expressed in this manner or some variation of it. While this is certainly an intuitive representation for a robot configuration, it only contains information about a single configuration. This idea can be extended to represent the entire space of possible configurations as a hierarchical graph. In this representation, a configuration represents a vertex and an edge represents a valid reconfiguration action to move from one configuration to another.


{% include figure.html image="/images/blog/2026-09-04/configuration-space-graph.png" width="80%" caption="Configuration space heirarchical graph"%}


This representation has some nice properties. First, graph invariants have interpretable meaning on the configuration space graph. Graph distances can be used to represent how far apart two configurations are. Graph diameter represents the maximum number of required moves to switch between any two configurations. This means there is an upper bound on the number of reconfiguration actions that can ever be required for a desired reconfiguration. These are just a few of the intuitive measures that come from expressing configuration space as a hierarchical graph.


### What to Measure?


If we want to develop a set of metrics to compare MRRs, these metrics should be applicable to the set of **all** MRRs. MMRs come in a wide variety of shapes and sizes. Notably, because of their adaptive nature, there is no single task that all MMRs are designed to perform. It is for this reason that I want to find an appropriate metric (or set of metrics) to define reconfigurability itself. All MRRs reconfigure. It is the trait that defines them. This makes reconfigurability one of the few measures that could apply to all possible MRRs regardless of design goal.


### What is Reconfigurability?


This is a really hard question. While many researchers may have an intuitive idea of what reconfigurability means, there does not seem to be a measurable definition. There is no *reconfigurometer* that can be used to measure the reconfigurability of an MRR. In fact, a single "reconfigurability number" may not be appropriate, even if it were defined. This is because there are many potential concepts we may be trying to numerically capture when we talk about reconfigurability. This means that we may require a set of different metrics. For example, take the following potential metric:


$$\frac{\text{# of unique, reachable configurations}}{\text{# of modules}}$$


Maybe this metric gives some information about how *reconfigurable* a system is in the sense that a system that can reach more configurations with less modules should have a higher reconfigurability. Consider a second potential metric:


$$\frac{\text{configuration graph diameter}}{\text{# of modules}}$$


This metric would give information about how far apart the different configurations are in configuration space. If a system has a relatively smaller graph diameter with a relatively larger number of modules, perhaps it is more reconfigurable in the sense that it can reach more configurations with less reconfiguration actions.


Reconfigurability might also be related to time requirements. If two systems are identical except that one completes all reconfiguration actions twice as fast, is the faster system more reconfigurable?


The next step in this project should be to generate a set of potential metrics and measure if they capture the phenomenon we are trying to capture.


## Citations


[1] L. A. T. Vu, Z. Bi, D. Mueller, and N. Younis, “Modular Self-Configurable Robots—The State of the Art,” Actuators, vol. 12, no. 9, p. 361, Sep. 2023, doi: 10.3390/act12090361.


[2] J. Liu, X. Zhang, and G. Hao, “Survey on research and development of reconfigurable modular robots,” Advances in Mechanical Engineering, vol. 8, no. 8, p. 1687814016659597, Aug. 2016, doi: 10.1177/1687814016659597.


[3] H. Y. K. Lau, A. W. Y. Ko, and T. L. Lau, “The design of a representation and analysis method for modular self-reconfigurable robots,” Robotics and Computer-Integrated Manufacturing, vol. 24, no. 2, pp. 258–269, Apr. 2008, doi: 10.1016/j.rcim.2006.11.003.


[4] I.-M. Chen, S. H. Yeo, G. Chen, and G. Yang, “Kernel for Modular Robot Applications: Automatic Modeling Techniques,” The International Journal of Robotics Research, vol. 18, no. 2, pp. 225–242, Feb. 1999, doi: 10.1177/027836499901800207.


[5] P. Bhat, J. Kuffner, S. Goldstein, and S. Srinivasa, “Hierarchical Motion Planning for Self-reconfigurable Modular Robots,” in 2006 IEEE/RSJ International Conference on Intelligent Robots and Systems, Beijing, China: IEEE, Oct. 2006, pp. 886–891. doi: 10.1109/IROS.2006.281742.


[6] F. Hou and W.-M. Shen, “Graph-based optimal reconfiguration planning for self-reconfigurable robots,” Robotics and Autonomous Systems, vol. 62, no. 7, pp. 1047–1059, Jul. 2014, doi: 10.1016/j.robot.2013.06.014.


[7] A. Dutta, P. Dasgupta, and C. Nelson, “Distributed configuration formation with modular robots using (sub)graph isomorphism-based approach,” Auton Robot, vol. 43, no. 4, pp. 837–857, Apr. 2019, doi: 10.1007/s10514-018-9759-9.


[8] M. Park, S. Chitta, A. Teichman, and M. Yim, “Automatic Configuration Recognition Methods in Modular Robots,” The International Journal of Robotics Research, vol. 27, no. 3–4, pp. 403–421, Mar. 2008, doi: 10.1177/0278364907089350.





