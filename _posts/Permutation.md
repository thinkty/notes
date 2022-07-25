---
category: algorithms
---

# Permutation
Given an array of numbers/letters, find all possible permutations.
The implementation below uses [backtracking](https://www.baeldung.com/cs/backtracking-algorithms), which is a brute force algorithm to find all solutions to a problem.

###### Implementation
```
vector<vector<int>> permute(vector<int>& nums) {
	vector<vector<int>> ans; 
	solve(ans, nums, 0); 
	return ans; 
}

void solve(vector<vector<int>>& ans, vector<int>& nums, int index){
	// Base Condition
	if(index == nums.size()) {
		ans.push_back(nums);
		return;
	}
	
	for(int i = index; i < nums.size(); i++) {
		swap(nums[i], nums[index]);
		solve(ans, nums, index + 1);
		swap(nums[i], nums[index]);
	}
}
```

In the recursive function, it basically finds all possible permutations by swapping one element with another and then swap it back to move on to the next one.

For example, given an array `[1, 2, 3]`, the steps are as follows:
```
index: 0, i: 0, arr: [1, 2, 3] → [1, 2, 3]

	index: 1, i': 1, arr: [1, 2, 3] → [1, 2, 3]
	
		index: 2, i'': 2, arr: [1, 2, 3] → [1, 2, 3]
		
	index: 1, i': 2, arr: [1, 2, 3] → [1, 3, 2]
	
		index: 2, i'': 2, arr: [1, 3, 2] → [1, 3, 2]
		
index: 0, i: 1, arr: [1, 2, 3] → [2, 1, 3]

	index: 1, i': 1, arr: [2, 1, 3] → [2, 1, 3]
	
		index: 2, i'': 2, arr: [2, 1, 3] → [2, 1, 3]
		
	index: 1, i': 2, arr: [2, 1, 3] → [2, 3, 1]
	
		index: 2, i'': 2, arr: [2, 3, 1] → [2, 3, 1]
		
index: 0, i: 2, arr: [1, 2, 3] → [3, 2, 1]

	index: 1, i': 1, arr: [3, 2, 1] → [3, 2, 1]
	
		index: 2, i'': 2, arr: [3, 2, 1] → [3, 2, 1]
		
	index: 1, i': 2, arr: [3, 2, 1] → [3, 1, 2]
	
		index: 2, i'': 2, arr: [3, 1, 2] → [3, 1, 2]
		

answer => [1, 2, 3] [1, 3, 2] [2, 1, 3] [2, 3, 1] [3, 2, 1] [3, 1, 2]
```