# Minimum Spanning Tree

![wikipedia image](minimum-spanning-tree.png)
A minimum spanning tree is a subset of the edges of a [connected](https://en.wikipedia.org/wiki/Connected_graph "Connected graph"), edge-weighted undirected graph that connects all the [vertices](https://en.wikipedia.org/wiki/Vertex_(graph_theory) "Vertex (graph theory)") together, without any [cycles](https://en.wikipedia.org/wiki/Cycle_(graph_theory) "Cycle (graph theory)") and with the minimum possible total edge weight.

##### Algorithms for finding the MST

###### Prim's Algorithm
Greedy approach to finding the MST. The time complexity changes based on the graph datastructure. See the [wiki](https://en.wikipedia.org/wiki/Prim%27s_algorithm#Time_complexity) for more info.
![demo](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/PrimAlgDemo.gif/300px-PrimAlgDemo.gif)
1. Start with the lowest weighted edge
2. From there, connect to an adjacent edge which has the lowest weight and it shouldn't connect two vertices that are already in the spanning tree
3. Repeat step 2 until all vertices are in the spanning tree

###### Kruskal's Algorithm
Greedy approach to finding the MST. The time complexity is _O_(_E_ log _E_) = _O_(_E_ log _V_) since E has a maximum value of V^2 and _log V^2_ = _2 log V_ = _O(log V)_.
![demo](https://upload.wikimedia.org/wikipedia/commons/b/bb/KruskalDemo.gif)
1. Sort all edges by weight : _O(E log E)_
2. Choose the lowest edge : _O(1)_
3. Check that it doesn't connect to an already connected vertex : _O(log E)_ using disjoint set
4. Repeat step 2 until all vertices are in the spanning tree : _O(E)_

###### Using Cayley's Formula (Complete Graph)
Given a [complete graph](https://en.wikipedia.org/wiki/Complete_graph), the number of spanning trees would be V^(V-2) where V is the number of vertices. Then, comparing the total weight of edges of the spanning trees would give an answer

Pseudocode from [Baeldung](https://www.baeldung.com/cs/graphs-total-number-of-minimum-spanning-trees#1-when-the-graph-is-a-complete-graph)

