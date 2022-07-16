# Depth First Search
This algorithm is used for iterating/searching a tree/graph data structure using a queue (FIFO).

###### Implementation
- Using a stack
```
TreeNode {
	int val
	TreeNode left
	TreeNode right
}

// This assumes that there are no cycles

dfs(TreeNode root) {
	stack.push(root)
	
	while (!stack.empty()) {
		TreeNode node = stack.pop()
		
		if (node->left)
			stack.push(node->left)
		if (node->right)
			stack.push(node->right)
	}
}
```

- Recursive implementation of searching for a certain target value
```
TreeNode {
	int val
	TreeNode left
	TreeNode right
}

dfs(TreeNode node, int target) {

	// Base case (end of search)
	if (node == NULL) {
		return -1
	}
	
	// Base case (found target)
	if (target == node->val) {
		return target
	}

	return dfs(node->left, target) && dfs(node->right, target)
}
```
The implementation above can have varying return values.
When implementing recursive algorithms, one must watch for stack overflow due to excessively deep recursions or infinite recursions. Some compilers optimize [tail recursion](https://xlinux.nist.gov/dads/HTML/tailRecursion.html) .

