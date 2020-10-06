# Graphs

{% hint style="info" %}
This is a second introduction to graphs that assumes you've at least seen them before. Take a look at the [61B version](https://cs61b.bencuan.me/abstract-data-types/graphs) if you feel lost!
{% endhint %}

## What's a graph?

Formally, a graph is a **set of vertices with a set of edges connecting them.** A graph can be defined as $$G = (V, E)$$ where $$V = \{A, B, \cdots V_n\}$$ and $$E = \{\{A, B\}, \{B, C\} \cdots \}$$

For an **ordered graph** where vertices are numbered, $$E$$could be represented as a set of ordered pairs instead: $$E = \{(A, B), (B, C) \cdots \}$$



### Concepts and Definitions

A **neighbor** of a vertex is another vertex that is next to the original vertex. Formally u is a neighbor of v if $$\{u, v\} \in E$$.

An edge is **incident** to the two vertices that it connects

The **degree** of a vertex is the number of other vertices neighboring. If the graph is directed, the degree can be split into the **in-degree** \(number of incoming connections\) and the **out-degree** \(number of outgoing connections\).

* The sum of vertex degrees is equal to $$2 |E|$$.
  * Proof: Count the number of incidences. Each edge is incident to exactly two vertices, so the total number of edge-vertex incidences is $$2|E|$$\(i.e. two times the number of edges\). 
  * The degree can also be defined as the number of incidences corresponding to a particular vertex v. Therefore, the total incidences is the sum of all degrees for all vertices!

A **path** is a sequence of edges. These edges must be connected, i.e. a path could be $$(v_1, v_2), (v_2, v_3), (v_3, v_4)$$.

* If there are $$k$$vertices, then a path should have $$k-1$$edges!

A **cycle** is a special path that begins and ends on the same vertex.

* Unlike a noncyclic path, there should be the same number of vertices as edges in a cycle.

A **walk** is a sequence of edges that could possibly repeat a vertex or edge.

A **tour** is a walk that starts and ends on the same nodes. Additionally, it cannot have any repeated edges.

* An **Eulerian walk** is a walk that uses **every edge** exactly once.
  * Doesn't require all vertices to be connected! There could be an isolated vertex with 0 degree.
* An **Eulerian tour** is a tour that visits **every edge** in a graph exactly once**.**
  * Theorem: any undirected graph has an Eulerian tour if and only if all vertices have **even degree** and is connected.
  * Proof: You need to use two incident edges every time you visit a node \(to enter and leave\). So when you enter, you need another edge to be able to leave! If a vertex has an odd number of edges, then you get stuck on that vertex with nowhere to go once you visit it.

Two vertices $$u$$and $$v$$are **connected** if there exists a **path** between them.

* If all vertices are connected, then the graph is considered a **connected graph.**

\*\*\*\*

A **complete graph** is a graph where every vertex is connected to every other vertex by exactly one edge. Complete graphs have some nice properties:

* Every vertex is incident to $$n-1$$edges \(if there are $$n$$total vertices\).
* The sum of all degrees is $$n(n-1)$$.
* The opposite of a complete graph is a **tree** that has the minimum number of edges \($$n-1$$ total\).
  * Trees are **acyclic** and **connected.**
  * **Leaves** are vertices that have degree 1.
  * The **root** is a single vertex that has degree 2.
  * **Non-leaf vertices** have degree 3.
* They can also be represented as **hypercubes** if they have $$2^n$$vertices and $$n2^{n-1}$$edges.
  * Hypercube cut property: For any cut \(S, V-S\) in a hypercube \(one that splits it into two subcubes\), the number of cut edges is at least the size of the small cube.

## Planar Graphs

A **planar graph** is a graph that can be drawn without having two edges overlap:

**Euler's Formula** states that a connected planar graph has two more vertices and faces than the number of edges:

$$
v + f = e + 2
$$

Let's take a look at some examples to convince ourselves of how this works:

\(A triangle has 3 edges and two faces: the inner face and outer face.\)

\(This shape is connected, but there is no enclosed face so the only face is the outer face.\)



Another consequence of Euler's Formula is the inequality that holds for connected planar graphs:

$$
3f \le 2e
$$

This inequality states that any planar graph with 2 or more vertices must have at most 3 faces for every 2 edges. We know this because the smallest possible face is a triangle. If we plug this into Euler's Formula, we can eliminate one variable to get $$e \le 3v - 6$$. This makes it much easier to figure out if a graph is planar or not, since faces are often difficult to count.



### Proof of Euler's Formula

Let's use induction!

**Base Case:** Let there be 0 edges and 1 vertex. This means there's only 1 \(outer\) face as well. In this case, $$v + f = 1 + 1 = 0 + 2$$. This works!

**Induction Step:**   
Let's consider the case of a tree. Then, we know that there are always 1 fewer edges than vertices, and only one face:  
$$v + 1 = (v-1) + 2$$ works!

What about something that's not a tree? Well, things get a bit tricker here.

* Let's consider a graph:
* Now, let's start with the tree corresponding to the same number of vertices as the original:
* Now, we'll keep adding edges to enclose faces until we reach the number of edges in the original:
* We'll notice here that for every edge we add, a new face is created!
* Therefore, we can plug this fact into our inductive hypothesis \(that Euler's formula works\) to get $$v + (f+1) = (e+1) + 2$$.

## Graph Coloring

A **graph coloring** assigns a color to each vertex such that every edge has two different colors on its two endpoints:

Often, we would like to figure out the **minimum number of colors** it takes to properly color a graph.

### Six Color Theorem

Let's propose that every graph can be colored with 6 colors or less. 

From Euler's Formula, recall that $$e \le 3v - 6$$for any planar graph with more than 2 vertices. We also know that the degree of the graph is equal to $$2e$$.

So, the average degree of any given vertex is $$\frac{2e}{v} \le \frac{2(3v-6)}{v} \le 6 - \frac{12}{v}$$. This proves that there **exists** a vertex with degree at most 5 \(due to the property of averages\). Let's try removing this vertex and see what happens.

Well, now each of the 5 neighbors each are assigned a different color. If we add the vertex back, then it can assume the 6th color. We can use this proof inductively to show that adding any vertex will result in the same thing occurring.



