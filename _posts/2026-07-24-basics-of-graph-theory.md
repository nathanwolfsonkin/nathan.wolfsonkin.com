---
title: Basics of Graph Theory
tags:
    - graph theory
---

Currently, I hold two degrees. A bachelor's degree in mechanical engineering from New York Institute of Technology and a master's degree in mechanical engineering from The Cooper Union. Now I am pursuing my PhD in mechanical engineering at Temple University. I am not sure if this is common among other people who hold degrees solely in mechanical engineering, but I somehow never formally learned any graph theory. I am familiar with lots of other disciplines in math: linear algebra, differential equations, probability, etc. I have used graphs to a certain extent, but never formally studied the basics.

Currently I am pursuing a project relating to metric development for modular robotics and I believe that the right level of abstraction for analysis of the set of modular robotic teams may be using a graph representation. To further my goal of unifying the modular robotics field with metrology, I have decided to learn the fundamentals of graph theory so I may be better equipped to tackle this problem. This post is just a review of basic graph theory as I understand it right now. All images and references are attributed to Robert J. Wilson's Introduction to Graph Theory [1].

## Graph Theory

Graph theory is a field of mathematics centering around points, called vertices, connected to each other via lines, called edges. This general formulation of vertices connected by edges can represent lots of things including, but not limited to, electrical networks, roads, and molecules. Importantly, it is also a very intuitive representation for teams of modular robots. Each robot and connection between robots can be represented as vertices and edges respectively.

## Basics

Graphs are fundamentally defined by two sets: the vertex-set $V(G)$ and the edge-set $E(G)$. $V(G)$ contains all of the vertices of $G$. $E(G)$ contains all of the edges connecting those vertices. The figure below shows a simple graph and a general graph. A simple graph is defined as a graph which contains no loops or multiple edges. A loop is an edge which connects a vertex to itself. Multiple edges are edges which connect the same vertices in the same graph.

{% capture left %}
{% include figure.html image="/images/blog/2026-07-24/simple-graph.png" width="100%" caption="A simple graph"%}
{% endcapture %}

{% capture right %}
{% include figure.html image="/images/blog/2026-07-24/general-graph.png" width="100%" caption="A general graph"%}
{% endcapture %}

{% include cols.html
  col1=left
  col2=right
%}

### Isomorphism

While graphs are commonly expressed as points connected by lines on a 2D plane, this is a representation of convenience. Unless explicitly stated, vertices have no position, nor relation to any other vertices besides the connection via an edge. For this reason multiple graphs can be said to be isomorphic if they could represent the same graph. The figure below shows two seemingly different graphs. The vertices of these graphs could be labeled such that all of the edges connect the same vertices, therefore the graphs are isomorphic.

{% include figure.html image="/images/blog/2026-07-24/isomorphic.png" width="100%" caption="Isomorphic graphs"%}

### Adjacency and Degrees

The degree of a vertex, $\delta(V)$, is the number of edges incident with $V$. Two vertices are said to be adjacent if they are connected by an edge. Two edges are said to be adjacent if they are incident with the same vertex.

{% include figure.html image="/images/blog/2026-07-24/adjacent.png" width="50%" caption=""%}

### Matrix Representations

It is sometimes convenient to be able to represent a graph as a matrix. The adjacency matrix and the incidence matrix are two examples of such. Assume a graph has $n$ labeled vertices and $m$ labeled edges.

{% include figure.html image="/images/blog/2026-07-24/matrix-rep.png" width="30%" caption=""%}

The adjacency matrix, $A$, is an $n \times n$ matrix where the $ijth$ column represents the number of connections between vertices $i$ and $j$. The adjacency matrix for the example matrix above is expressed as:

$$A = \begin{bmatrix}0 & 1 & 0 & 1 \\ 1 & 0 & 1 & 2 \\ 0 & 1 & 0 & 1 \\ 1 & 2 & 1 & 0 \end{bmatrix}$$

The incidence matrix, $M$, is an $n \times m$ matrix  where the $ijth$ entry is a binary entry expressing if edge $m$ is connected to vertex $i$ or not. Each column, $j$, of $M$ represents an edge. The rows in an individual column represent the vertices that the edge is connecting. The incidence matrix for the example matrix above is expressed as:

$$M = \begin{bmatrix}1 & 0 & 0 & 1 & 0 & 0 \\ 1 & 1 & 0 & 0 & 1 & 1 \\ 0 & 1 & 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 1 & 1 & 1 \end{bmatrix}$$

## Connectivity

One of the big questions in modular robotics that I am interested in tackling is defining reconfigurability. I think it is possible that the connectivity of the representative graph may be critical for creating this definition. There are a few different types of connectivity most of which are based on the idea of a walk.

### Types of Walks

A walk is a sequence of edges where any two consecutive edges are adjacent or identical. One particular walk for the graph below can be denoted as such:

$$v \rightarrow w \rightarrow x \rightarrow y \rightarrow z \rightarrow z \rightarrow y \rightarrow w $$

{% include figure.html image="/images/blog/2026-07-24/walk.png" width="50%" caption="Example graph"%}

There are many different classes of walks based on if edges can be repeated, if vertices can be repeated, and if the starting and ending vertices are the same. The table below outlines these classifications

| Classification | Required to be closed? (Final vertex = initial vertex) | Allows repeated edges? | Allows repeated vertices? (excluding first and last) |
|---|---|
| Walk | $\times$ | $\checkmark$ | $\checkmark$ |
| Trail | $\times$ | $\times$ | $\checkmark$ |
| Path | $\times$ | $\times$ | $\times$ |
| Cycle | $\checkmark$ | $\times$ | $\times$ |

### Length

The length of a walk is the magnitude associated with the walk. If the graph is weighted, each edge adds the value of its weight. In the case of an unweighted graph, the walk length is equal to the number of edges. 

### Connectivity

The "connectedness" of a graph can be measured by the number of edges required to be removed to disconnect the graph. Any set of edges that disconnects a graph is called a disconnecting set. A minimal disconnecting set that contains no proper subset that is also a disconnecting set is a cutset. Take the example graph below:

{% include figure.html image="/images/blog/2026-07-24/disconnecting-set.png" width="50%" caption=""%}

Some disconnecting sets of this graph include:

| $ \{ e_1, e_2 \} $ | Cutset |
| $ \{ e_3,e_6,e_7,e_8 \} $ | Cutset |
| $ \{ e_1,e_2,e_5 \} $ | Disconnecting Set |

Similarly we can define a separating set as a set of vertices whose removal disconnects the graph. Some examples of separating sets in this graph include:

| $ \{ w, x \} $ | Separating Set |
| $ \{ w, x, y \} $ | Separating Set |

### Connectivity

The edge connectivity of a graph, $\lambda(G)$, is defined as the size of the smallest cutset. The edge connectivity of the example graph above is $\lambda(G)=2$. It can also be said that G is 2-edge-connected.

Similarly, vertex connectivity, $\kappa(G)$, is defined as the smallest separating set. The vertex connectivity of the example graph above is $\kappa(G)=2$. It can also be said to be 2-vertex-connected.

For any connected graph:

$$\kappa(G) \leq \lambda(G) \leq \delta(G) $$

## Citations

[1] R. J. Wilson, Introduction to graph theory. 5th Edition
