---
title: Ontology of Modular Reconfigurable Robots and Representations as Graphs
tags:
   - modular-robotics
   - metrology
   - graph-theory
---

In my research, my current objective is to define what it means for a modular reconfigurable robot (MRR) to be reconfigurable. The whole field is built around the idea of building reconfigurable robots, but nobody has rigorously defined what that means. To that end, I am currently studying the definitions and differentiations that do exist in this space. A survey paper from 2025 [1] defines the following categories for MRRs:

| Category | Definition |
|---|---|
| Classification | The type of structures that the MRR can collectively configure into: Lattice, mobile, truss, chain, or freeform |
| Connections per connector | one-to-one (mono) or many-to-one (poly) |
| Actuator types | Joint actuators, spatial actuators, or both |
| Homogeneity | Homogenous or Heterogenous |
| Connection Technology | Technology used to connect modules: Mechanical, Magnetic, Velcro, etc. |
| Joint degrees of freedom | The number of degrees of freedom associated with the joint actuator |
| Spatial degrees of freedom | The number of degrees of freedom associated with the spatial actuation |
| Workspace | Number of spatial dimensions which the MRR team works: 2D or 3D |
| Self-reconfiguration | Can the MRR team reconfigure itself? |
| Self assembly | Can the MRR team assemble itself? |

While this is not seen in the literature, I have been thinking about further classifying these groups into two categories: structural and operational. These classifications serve to separate descriptive categories into whether they affect the space of unique graph representations that can be reached (structural) or if they affect how the MRR switches from one configuration to another (operational). The reason for this distinction is that at the graph based abstraction level of an MRR, the mechanisms are irrelevant. If one MRR uses velcro for its connection mechanism, but another uses electromagnets, the graph representing them should be structurally the same. I want to see if reconfigurability can be defined primarily based on the graph representation of MRRs. The next sections will explain the structural categories and how they relate to graphs.

### Graph Representation

It is common to represent MRRs as graphs. In graph representation, each node represents a module and each edge represents a connection between modules. In this sense, most graph representations of MRRs are simple graphs because no two modules should need to have multiple independent connections (multiple edges) and there should be no connection between a module and itself (loops).

{% capture left %}
{% include figure.html image="/images/blog/2026-07-31/simple-graph.png" width="80%" caption="A simple graph"%}
{% endcapture %}

{% capture right %}
{% include figure.html image="/images/blog/2026-07-31/general-graph.png" width="80%" caption="A general graph"%}
{% endcapture %}

{% include cols.html
 col1=left
 col2=right
%}

### Classification

This is likely the most interesting category. The idea here is that MRRs can largely fit into one or more of the following categories: lattice, chain, mobile, truss, or freeform. The table below shows the relative amount of each robots that exist in each class:

|Class|% of total systems from 1985-2023 [1]|
|-|-|
|Lattice|$66.67 \%$|
|Chain|$55.56 \%$|
|Mobile|$48.15\%$|
|Freeform|$12.35\%$|
|Truss|$6.17\%$|

**Lattice**
- Lattice-type MRRs are defined by the modules being organized into regular, repeating grids.
- In graph representation, they can be represented by a lattice graph.

{% include figure.html image="/images/blog/2026-07-31/lattice-graph.webp" width="20%" caption="A square lattice graph [2]"%}

**Chain**
- Chain-type MRRs are systems where modules are connected serially to form a chain or branching morphology.
- In graph representation, chain-type MRRs are represented as trees.

{% include figure.html image="/images/blog/2026-07-31/tree-graph.webp" width="20%" caption="A labeled tree graph [3]"%}

**Mobile**
- Mobile-type MRR systems differentiate themselves by having the ability of each module to independently move.
- In graph representation, a mobile-type MRR system would be represented as the union of multiple graphs, oftentimes including the $N_1$ null graphs during reconfiguration since modules would move independently.

**Truss**
- "Truss-type MRR systems consist of interconnectable beams, nodes, or struts, forming a morphology that resembles a truss." [1]
- I am not sure that the graph representation for the general truss-type MRR can be easily categorized like the others.

**Freeform**
- "Freeform-type MRR systems focus on the connecting capabilities, enabling connections between modules to be established from all positions and orientations. Circular and spherical mechanisms are often employed to achieve this unlimited range of connection  characteristics." [1]
- Similar to truss-type MRRs, it is not clear that freeform-type MRRs have any sort of inherent graph structure that is common to the set of all MRRs.

### Connectivity

Connectivity is defined as monogamous or polygamous. A monogamous connector connects one module to a single other module. A polygamous connector connects one module to one or more different modules. I am not quite sure how to represent this in graph theory terms yet. An edge by definition connects a single node to a single other node. Perhaps a polygamous connector can be represented as a different type of node which is adjacent to each of the modules it connects. 

### Homogeneity

Homogenous MRRs are MRRs that have all identical modules. The advantage here is that in theory, these can be mass manufactured at low prices. Heterogenous MRRs use multiple different types of modules. In graph representation this might be represented as different types of nodes. For example in graph based SLAM algorithms, robot poses are represented by one type of node and landmark poses are represented by another. This could use a similar system.

### Workspace

Workspace for MRRs is either 2D or 3D. In graph representations, 2D workspace MRRs would be representable as planar graphs. I am unclear on if this would yield any tangible benefit at the moment.

## Citations

[1] G. Liang, D. Wu, Y. Tu, and L. Tin Lun, “Decoding Modular Reconfigurable Robots - A Survey on Mechanisms and Design,” The International Journal of Robotics Research, vol. 44(5) 740–767, 2025, doi: 10.1177/02783649241283847.

[2] https://en.wikipedia.org/wiki/Lattice_graph

[3] https://en.wikipedia.org/wiki/Tree_(graph_theory)
