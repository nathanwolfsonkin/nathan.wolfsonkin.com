---
title: Modular Robotics and Metrics
tags:
 - Multi-Robot Systems
 - Dimensional Analysis
 - Modular Robotics
image: /images/blog/2026-07-17/taxonomy.png
---

Modular robotics is a exciting field. The idea is that instead of having a single robot built for a single purpose, we can instead use a team of modular robots. These modular robots would be able to work together, connecting and building off of each other to achieve unparalleled adaptability. This is actually a common approach in biology. Cells can be thought of as modular biological entities which form together to perform actions beyond the capability of any individual cell. 

A particular part of modular robotics that I have found interesting as of late is the self-reconfiguring modular robot. The idea here is that a team of modular robots could change and adapt to accomplish whatever task they are currently pursuing. This is a concept that is not new in science fiction. While I am sure there are older examples, my favorite is from the Pixar movie Big Hero 6. Here, modular robots called microbots are invented. These microbots can work together to form massive structures.

{% include figure.html
 image="/images/blog/2026-07-17/microbots.gif"
 width="40%"
 caption="Microbots reconfiguring (source: [Gifer](https://gifer.com/en/V24E))"
%}

Self-reconfiguring modular robots have a particular set of advantageous characteristics that set them apart from traditional teams of mobile robots. While implementation is still somewhat crude, the ultimate goal is that self-reconfiguring modular robotics will be more versatile, robust, and cheaper than traditional robots [1]. 
1. Versatility
 - Self-reconfigurable systems will allow for more potential tasks than a regular robot. Imagine a locomotion context. If there is rugged terrain, the modular system might configure itself into a legged robot. If there are roads, perhaps a wheeled system will be energetically superior. 
2. Robustness
 - Self-reconfigurable systems will be able to handle failures by working around the faulty module. If a single module fails, the remainder of the modules can simply disconnect it and continue on with the objective.
3. Low Cost
 - Self-reconfigurable robots will be lower cost because mass production of a single robot thousands, millions, or billions of times will allow for economies of scale to optimize the manufacturing process.

## A Bit of History and the Need for Metrology

Work on modular robotic systems is traced back to the cellular robotic system (CEBOT) [2] which published in 1989. Most work since then has focused on various mechanical implementations. The taxonomy used across the field is somewhat consistent [3], but looking back thirty-six years it seems that this is a fairly fractured field. There are no real quantitative measures for traits shared by every system. Ideas like reconfigurability and adaptability are the motivating ideas behind the entire field, yet we still lack any real way of quantifying them. Instead, qualitative comparisons are used in survey papers to differentiate self-reconfigurable modular robots [3]. 

{% include figure.html
 image="/images/blog/2026-07-17/taxonomy.png"
 width="50%"
 caption="Taxonomy of Self-Reconfigurable Modular Robots [3]"
%}

A survey paper from 2023 [5] states the functional requirements for homogenous modular self-configurable robot as follows:

| Functional Requirement | Expectation |
|---|---|
| Size | As small as possible |
| Mechanical strength | Safety and reliability |
| Load capacity to module weight | As high as possible |
| Information sharing | Ability to transmit |
| Power sharing | Ability to transmit |
| Reversibility and repeatability | Should be reversible and repeatable |
| Docking/undocking speed | As fast as possible in both procedures |
| Tolerance to misalignment | Should be high |
| Power consumption | As little as possible to no power consumption |
| Gender and orientation | Should be genderless and orientation-invariant |
| One-sided connection | Ability to create connection from one side |
| Cost | As low as possible |

It is important to note that there are no quantitative measurements. Everything in this field is described qualitatively. The closest thing to quantitative analysis of the state of this field came from the same survey paper [5] when it compared different docking mechanisms:

{% include figure.html
 image="/images/blog/2026-07-17/docking-table.png"
 width="100%"
 caption="Docking Function Requirements [5]"
%}

Even here the comparisons are fairly surface level. Yes I can see which one has better mechanical strength or load capacity to module weight ratio. But the question arises: which of these connection mechanisms allows for better reconfigurability? Which allows for better adaptability? 

Self-configuring modular robotics is a field which is in dire need of unification. Metrology is the key. Identification and establishment of metrics will finally allow for quantitative comparisons across the field. There have been attempts at this endeavor. Liu et al. proposed the evolutionary cobweb evaluation model of autonomy [6]. The problem with a system like this is it is somewhat contrived. It does prescribe a number to the autonomy of each modular robotic system, but the number is fabricated. It is influenced by weights that the author arbitrarily assigned to different systems. For example, one of the characteristics to describe model autonomy is the "module motion attribute" which ranks modules on a scale as follows:

| 0 | none |
| 1 | mobile |
| 2 | rotation |
| 3 | translation |
| 4 | manipulation |
| 5 | fly |

It is not clear to me that the ability of a module to fly implies that it is five times more autonomous than a mobile module. The point here is that while defining process to measure autonomy is important, it is just as important that the process is rigorous. 

More developed fields of study, like fluid mechanics, have worked on this. Reynolds number, for example, is a dimensionless number based on the ratio of inertial to viscous forces in a flow. Importantly, Reynolds number predicts whether a flow is laminar or turbulent. Modular robotics needs our own Reynolds number. A latent variable to be discovered which can be used to define and identify the reconfigurability, robustness, or autonomy of a modular robotic system.

## Citations
[1] M. Yim et al., “Modular Self-Reconfigurable Robot Systems [Grand Challenges of Robotics],” Robotics & Automation Magazine, IEEE, vol. 14, pp. 43–52, Apr. 2007, doi: 10.1109/MRA.2007.339623.

[2] Fukuda T, Nakagawa S, Kawauchi Y, Buss M. 1989. Structure decision method for self organising robots  based on cell structures-CEBOT. In 1989 IEEE International Conference on Robotics and Automation, Vol. 2, pp. 695–700. New York: IEEE

[3] L. A. T. Vu, Z. Bi, D. Mueller, and N. Younis, “Modular Self-Configurable Robots—The State of the Art,” Actuators, vol. 12, no. 9, p. 361, Sep. 2023, doi: 10.3390/act12090361.

[4] “Self-Reconfiguring Modular Robot.” [Online]. Available: https://en.wikipedia.org/wiki/Self-reconfiguring_modular_robot

[5] L. A. T. Vu, Z. Bi, D. Mueller, and N. Younis, “Modular Self-Configurable Robots—The State of the Art,” Actuators, vol. 12, no. 9, p. 361, Sep. 2023, doi: 10.3390/act12090361.

[6] J. Liu, X. Zhang, and G. Hao, “Survey on research and development of reconfigurable modular robots,” Advances in Mechanical Engineering, vol. 8, no. 8, p. 1687814016659597, Aug. 2016, doi: 10.1177/1687814016659597.
