# Graphs

{% hint style="info" %}
This is a second introduction to graphs that assumes you've at least seen them before. Take a look at the [61B version](https://cs61b.bencuan.me/abstract-data-types/graphs) if you feel lost!
{% endhint %}

### What's a graph?

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



