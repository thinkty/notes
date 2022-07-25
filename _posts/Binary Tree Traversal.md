---
category: algorithms
---

# Binary Tree Traversal

![[binary-tree-example.png]]

- Inorder : B - A - C
	- Useful for getting the non-decending array of the tree.
- Preorder : A - B - C
	- Topogically sorted as parent node is firt processed.
- Postorder : B - C - A
	- Useful for getting postfix expression of a binary expression tree.

The orders can go from left child to right child and vice versa.

###### Implementation
```
TreeNode {
	int val
	TreeNode left
	TreeNode right
}
```

- Inorder (iterative)
```
inorder(TreeNode * root) {

	TreeNode * trvlr = root
	
	while (trvlr || !stack.empty()) {
		
		// From the current node, iterate to the "left-most" node
		while (trvlr) {
			stack.push(trvlr)
			trvlr = trvlr->left
		}
		
		// Parent node
		trvlr = stack.pop()
		
		// Right node
		trvlr = trvlr->right
	}
}
```

- Inorder (recursive)
```
inorder(TreeNode * node) {
	// Base case
	if (node == NULL) {
		return
	}

	// Left
	inorder(node->left)
	
	// Center
	node->val
	
	// Right
	inorder(node->right)
}
```
