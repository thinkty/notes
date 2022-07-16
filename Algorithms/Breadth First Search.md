# Breadth First Search
This algorithm is used for iterating/searching a tree/graph data structure using a stack (LIFO).

###### Implementation
```
TreeNode {
	int val
	TreeNode left
	TreeNode right
}

// This assumes that there are no cycles

bfs(TreeNode root) {
	queue.enqueue(root)
	
	while (!q.empty()) {
		TreeNode n = queue.deque()
		
		if (n->left)
			queue.enqueue(n->left)
		if (n->right)
			queue.enqueue(n.right)
	}
}
```

