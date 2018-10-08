## Problem

Given an array of integers, return indices of the two numbers such that they add up to a specific target. You may assume that each input would have exactly one solution, and you may not use the same element twice


Solution
```java

class Solution {
	public int[] twoSum(int[] nums, int target) {
		Map<Integer, Integer> map = new HashMap<>();
		for(int i=0; i<nums.length; i++) {
			int num = nums[i];
			int t = target - num;
			if (map.containsKey(t)) {
				return new int[]{map.get(t), i};
			} else {
				map.put(nums[i], i);
			}
		}
		return new int[]{0,0};
	}
}

```
