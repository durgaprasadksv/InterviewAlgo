## Problem
Given a string, find the length of the longest substring without repeating characters.

## Solution

```Java


public class Solution {
	/*
		Idea: Don't use a map. Have a start index that points to the start of the 
		unique character string. By default it is set to 1 to mark string of length 1. 
		Take a 256 int array to store the last seen index of a character. 

		if you see the same character twice from your start point. take the max , update the start to next char
	*/
	public int lengthOfLongestSubstring(String s) {
		int[] arr = new int[256];
		int max = 0;
		for(int i=0,start=0 i<s.length(); i++) {
			char c = s.charAt(i);
			start = Math.max(start, arr[c]);
			max = Math.max(max, i-start+1);
			arr[c] = i+1;
		}
		return max;
	}
	
		
  	//using hash maps. 	
	public int lengthOfLongestSubstring(String s) {
		Map<Character, Integer> indexMap = new HashMap<>();
		int max = 0;
		for(int i=0,start=0; i<s.length(); i++) {
			char c = s.charAt(i);
			if (indexMap.containsKey(c) && (indexMap.get(c) >= start)) {
				start = indexMap.get(c)+1;
			}
			indexMap.put(c, i);
			max = Math.max(max, i-start+1);
		}
		return max;
	}
}

```
