---
title: Bees, ants, and more general swarms
tags:
  - Multi-Robot-Systems
  - Swarms
  - Bio-inspiration
---

I spent a good bit of this week reading about swarms. This was in part sparked by a good blog post I read by
[Jason Fantl](https://jasonfantl.com/posts/Bee-Swarm/) where talks about bio-inspired swarming algorithms that could roughly emulate the behavior of bee hive reproduction.


## Bee Hive Distributed Behaviors

This isn't necessarily directly related to robotics applications, but I think it's important to learn about efficient distributed systems without nessecarily having an application in mind.

### Splitting
In the springtime, honey bee colonies reproduce by splitting in two. Around two thirds of the worker bees and the old queen venture off to form a new hive while the other half stay in the existing hive. The interesting thing here is that this happens in an entirely distributed manner. There is no managerial class of bees deciding who goes where to ensure an even split. The process is so efficient that the splitting process itself only takes around 20 minutes [1].


### Nest Selection
Once the hive has been split, the leaving group must select a new hive location. The mechanism here is that scout bees will venture out to potential new locations. Upon returning to the hive, the scout will dance a particular pattern to vote for that hive location. An interesting note here is that it is unlikely that a single bee actually visits more than one location. The bees are not shopping around to see the best option. Instead a bee will dance for a longer period of time correlated with the quality of the proposed new nest location. Simultaneously, bees have a chance of being recruited by a particular dance. The output behavior is that a high quality nest site is reliably chosen in a purely distributed manner. [4, 5]


An interesting note is that since a single bee is unlikely to visit more than one location, the implication is that scout bees have some sort of instinct for judging potential hive sites objectively. Perhaps 'objectively' is the wrong word, but whatever scale they are using, it must be similar to the scale that is shared by the other scout bees to ensure assessments of hive quality are similar.


## Ants and the Internet
Also inspired by a [Jason Fantl post](https://jasonfantl.com/posts/Ants-Internet/).


Many ant species use pheromone trails to communicate two things: first that food is available and second where to find it. Forager ants (Pogonomyrmex barbatus) eat mostly scattered seeds which can be collected by a single ant. In this context, spatial information is not required so they do not use pheromone trails. While spatial information is not required, whether or not food exists at all is still information that is needed to regulate whether ants should be foraging or not. The question is then as follows: "How do forager ants determine whether or not they should be out foraging for food at all?" [6]


The mechanism is actually quite simple. When forager ants pass each other in the colony, they contact antennas. This brief moment is enough to tell whether an ant is currently holding food or not. If the ant passes many ants that are returning with food, it is likely that food is available and that ant will in turn begin foraging. If the ant passes few ants with food, the implication is that food is hard to come (perhaps no food around or predators) and the and will not go out foraging. [6]


This discrete feedback mechanism is actually seen in many biological and engineered systems. It is used to regulate the size of bacterial cells, neuron connections in brain development, and Transmission Control Protocol in networking [2]. The basic idea is that some optimal value (cell size, data rate, food foraging rate, etc. ) is unknown, but exists. To reach this optimal value, a task is attempted. If the measurement results in a success, the task is attempted more. In the TCP context, this means if a packet is successfully received, the data rate should be increased. If a packet is not received, the data rate should be reduced [2].


## Other Interesting Swarm Stuff
My friend and colleague, [Alkesh Srivastava](https://alkeshks.com/), sent me a paper he is currently attempting to publish [3] on a theory of information propagation in multi-robot systems. The paper proposes that information propagation in a swarm can be likened to collisions in kinetic theory.


The theory poses that information exchange in distributed multi robot systems is fundamentally limited by three factors:
1. Access Limit
 - Information is limited to the robots that directly sense it
2. Staleness Limit
 - Information is propagated, but loses value as the target moves
3. Geometry Limit
  - Target motion outpaces information propagations


These limits are evaluated in the context of a tracking problem. It is shown empirically that improvements in tracking error diminish if any of the above factors are restricted.

## Citations

[1] P. Rangel, “Colony Fissioning In Honey Bees: How Is Swarm Departure Triggered And What Determines Who Leaves?,” Apr. 2010, Accessed: Jun. 11, 2026. [Online]. Available: https://hdl.handle.net/1813/14898

[2] J. Y. Suen and S. Navlakha, “A feedback control principle common to several biological and engineered systems,” J R Soc Interface, vol. 19, no. 188, p. 20210711, Mar. 2022, doi: 10.1098/rsif.2021.0711.

[3] A. K. Srivastava and P. Dames, “A Kinetic Theory of Encounter-Based Information Propagation in Multi-Robot Systems”. (Not published yet)

[4] M. R. Myerscough, “Dancing for a decision: a matrix model for nest–site choice by honeybees,” Proc. R. Soc. Lond. B, vol. 270, no. 1515, pp. 577–582, Mar. 2003, doi: 10.1098/rspb.2002.2293.

[5] N. F. Britton, N. R. Franks, S. C. Pratt, and T. D. Seeley, “Deciding on a new home: how do honeybees agree?,” Proc. R. Soc. Lond. B, vol. 269, no. 1498, pp. 1383–1388, Jul. 2002, doi: 10.1098/rspb.2002.2001.

[6] B. Prabhakar, K. N. Dektar, and D. M. Gordon, “The Regulation of Ant Colony Foraging Activity without Spatial Information,” PLOS Computational Biology, vol. 8, no. 8, p. e1002670, Aug. 2012, doi: 10.1371/journal.pcbi.1002670.