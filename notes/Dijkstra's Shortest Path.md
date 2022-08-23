# Dijkstra's Shortest Path
Dijkstra's algorithm is used to find the shortest path between nodes in the graph.
There are many variations of this algorithm as it can find the shortest path between the source node and not only the destination node, but also all the other nodes `shortest path tree`.

![Image from wikipedia](https://upload.wikimedia.org/wikipedia/commons/5/57/Dijkstra_Animation.gif)

###### Implementation
The time complexity differs by the data structures used. The time complexity can have the worst case of _O(E log V)_.
Given a directed & weighted graph in some sort of input, or just the source node and the destination node, the following steps are taken to perform the algorithm.

1. To initialize, create the following data structures:
	- `hash set` that represents the visited nodes.
	- `hash map` that keeps track of distance from the source node to all the nodes in the graph (including the source node). Since the distance is unknown, it is initialized to the maximum value (a.k.a infinite), but for the source node, it is set to 0 since the distance from itself is 0.
	- `priority queue` implemented with a `min heap` that will keep track of which nodes to check next. The queue will be initialized with only the source node inserted.
	- Optional `hashmap` to keep in track of the shortest path. This map will track all nodes and the values will be the node that connects to the node of matter. This way, by updating this map when the distance `hash map` is updated, it can keep not only the shortest distance but also the actual path.

2. Get the current node from the top of the `priority queue`. For each node that are *unvisited* and *connected* ( = can go from the current node), calculate the distance from the current node to the node by looking up the `hash map`. Get the current node's distance from the source node by `map[currentNode]` and add the distance from the current node to the connected node. If the newly calculated distance is smaller than the value of the connected node's distance from the source node  `map[node]`, update it.
 `
```
map[node] = min(map[node], distanceFromCurrentNode + map[currentNode])
```

3. After calculating the distance and updating the map if necessary, insert the connected node to the `priority queue` to visit later. After step 2 has been done to all the nodes connected to the current node, mark the current node as visited by adding to the `hash set` and repeat step 2 until the following condition is met:
	- Destination node is to be visited next (finding shortest path from source to destination)
	- Empty `priority queue` (finding shortest path to all other nodes including target node)

