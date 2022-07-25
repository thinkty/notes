# Two Sum
Given an array of integers and a target value, return two indices of elements that add up to the given target value.

###### Implementation
```
vector<int> twoSum(vector<int> nums, int target) {
	vector<int> ans;
	unordered_map<int, int> map;

	for (int i = 0; i < nums.size(); i++) {
		int otherNum = target - nums[i];
		
		if (map.find(otherNum) != map.end()) {
			ans.push_back(i);
			ans.push_back(map[otherNum]);
			return ans;	
		}
		
		map[nums[i]] = i;
	}
	
	return ans;
}
```

In the implementation above, we first find the appropriate value of the other number that, in addition with the current number, becomes the target value. 
```
int otherNum = target - nums[i]
```

If found, that is the answer.
If not found, save the current element's value as key and the index as value so that it can later be used to find the answer.