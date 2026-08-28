---
title: More Matrix Representations for Modular Robots
tags:
   - modular-robotics
   - graph-theory
---

Modular robots are commonly expressed as graphs with vertices representing modules and edges representing their connections. This is a good start, but there are more features that need to be included to fully describe the state of a modular robotic team. Oftentimes a module will have a set number of labeled ports. It is important to describe which ports are being utilized. Last week, I discussed how Chen and Burdick solved this problem with the assembly incidence matrix (AIM) [1]. Baarir et al. solved this problem using the port adjacency matrix. The basic idea is that it is similar to a normal adjacency matrix, but encodes port numbers into the matrix. This can be done because of the assumption that all graph representations for MRRs must be simple graphs. Consider the following MRR and graph below:

{% include figure.html image="/images/blog/2026-08-28/sample-bot-and-graph.png" width="80%" caption="Sample homogenous modular robot and accompanying graph [1]"%}

The adjacency matrix is:

$$A = \begin{bmatrix} 0 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \\ 1 & 0 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{bmatrix}$$

If we assume that all MRR graph representations will be simple graphs there will be no multiple connections, this means that the entries in this matrix will always be binary. Since the entries are binary, we can replace all of the $1$s with the port numbers that are occupied without losing any information about the connections.

The port adjacency matrix is:

$$A_P = \begin{bmatrix} 0 & 1 & 2 & 3 \\ 3 & 0 & 0 & 0 \\ 2 & 0 & 0 & 0 \\ 1 & 0 & 0 & 0 \end{bmatrix}$$

Note that the port numbers are not described in the graph, these numbers were chosen as an example to showcase that the port adjacency matrix does not retain the symmetric property that the adjacency matrix has.

Now it is also important to recognize that this representation is not very compact. This means that the size of the configuration space will scale exponentially with increasing $N$. To tackle this problem, Baarir et al. proposes a compact encoding of the state [2]. Here a single module of an MRR is represented by a vector containing the state of its ports and the state of its degrees of freedom.

$$\begin{bmatrix} p_1 & p_2 & ... & p_{final} & DoF_1 & DoF_2 & ... & DoF_{final}  \end{bmatrix}$$

The entire team can be represented by stacking these vectors into a matrix called the ports-connectivity matrix. For a homogenous MRR team with seven ports, one DoF, and five modules, the ports-connectivity matrix might look like this:

{% include figure.html image="/images/blog/2026-08-28/ports-connectivity-matrix.png" width="80%" caption="Ports connectivity matrix and associated MRR configuration [2]"%}

The $\alpha$ column notes the state of the single degree of freedom. The first row can be read as follows:

> Module 1 is connected to module 2 via port 4. Its actuator is at a position corresponding to 90.

> Module 2 is connected to modules 3, 1, and 4 via ports 4, 6, and 7 respectively. Its actuator is at a position corresponding to 90.

This encoding of MRR structure is powerful partly because it is compact, but also because it can be used to reveal isomorphic configurations. This requires a few steps:

1. Define an encoding alphabet which makes every local configuration unique
2. Encode the ports-connectivity matrix using this alphabet
3. Sort the rows of the symbolic ports-connectivity matrix

### Alphabet Definition

The first step is to define an alphabet which describes the local connectivity state of the module. This will, in general, require an additional bit for each port.

{% include figure.html image="/images/blog/2026-08-28/alphabet.png" width="80%" caption="Sample alphabet for a module with 3 ports [2]"%}

### Symbolic Encoding

Next, the local information is encoded into the ports-connectivity matrix. Entry is replaced with the symbol describing its local state.

{% include figure.html image="/images/blog/2026-08-28/symbolic-encoding.png" width="80%" caption="Sample configuration (left), ports-connectivity matrix (center), symbolic ports-connectivity matrix (right)"%}

The value of the symbolic encoding is that it decouples some of the data from its position in the matrix. Before, the matrix read:

> Module 1 is connected to module 3 via port 7.
> Module 3 is connected to modules 1, 4, 2, and 5 via ports 1, 4, 6 and 7 respectively.

With the symbolic encoding it instead reads:

> Module 1 is utilizing port 7.
> Module 3 is utilizing ports 1, 4, 6, and 7.

The information conveyed by each symbol removes non-local information.

### Canonization

The idea here is that any matrix with the same structure should represent an isomorphic configuration. So if we perform row permutation to sort the matrix, then all isomorphic configurations should look the same.

{% include figure.html image="/images/blog/2026-08-28/canonization.png" width="80%" caption="Canonization of the ports-connectivity symbolic matrix"%}

## Citations

[1] I.-M. Chen and J. W. Burdick, “Enumerating the nonisomorphic assembly configurations of modular robotic systems,” in Proceedings of 1993 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS ’93), Jul. 1993, pp. 1985–1992 vol.3. doi: 10.1109/IROS.1993.583905.

[2] S. Baarir, L. Hillah, F. Kordon, and E. Renault, “Self-reconfigurable Modular Robots and Their Symbolic Configuration Space,” vol. 6662, 2010, pp. 103–121. doi: 10.1007/978-3-642-21292-5_6.
