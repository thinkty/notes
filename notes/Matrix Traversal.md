---
category: algorithms
---

# Matrix Traversal
Matrix (or 2 dimensional array) can be traversed using BFS/DFS in O(**m × n**) where **m** and **n** are rows and columns (= number of cells in the matrix).

###### Implementation
```
traverse(vector<vector<int>> matrix) {
	queue<pair<int,int>> bfs;
	
	// Add starting points for traversal
	for (int i = 0; i < matrix.size(); i++) {
		for (int j = 0; j < matrix[i].size(); j++) {
			
			if (%% Some kind of condition %%) {
				bfs.push({ i, j });
			}
			
		}
	}
	
	// Traversal begin using bfs
	while (!bfs.empty()) {
		int x = bfs.front().first;
		int y = bfs.front().second;
		
		// Adding next points from top, bottom, left, right
		if (x > 0) {
			bfs.push({ x - 1, y });
		}
		if (x < matrix.size() - 1) {
			bfs.push({ x + 1, y });
		}
		if (y > 0) {
			bfs.push({ x, y - 1 });
		}
		if (y < matrix[x].size() - 1) {
			bfs.push({ x, y + 1 });
		}
	}
}
```

- There can be various conditions to adding the first starting points for traversal.
- During the actual traversal, BFS/DFS can be used in one place over other or even together for easier understanding.
- In some cases, one can utilize another matrix for recording which cells in the matrix has been visited so that the traversal doesn't end up in an infinite loop.
- When adding the next points (TOP, BOTTOM, LEFT, RIGHT), since that part is extremely repetitive, using a constant runtime loop might be a good idea.
