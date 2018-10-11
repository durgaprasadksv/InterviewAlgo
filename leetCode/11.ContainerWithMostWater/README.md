## Problem

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.


## Solution


``` Java

//Idea: we can do it in O(n^2) using two loops to examine all combinations. But we can do in O(n) with the following 
//observation. Take two pointers, one to start and one to end. Caculate volume of the container. Now to go the next best 
//possibility note that if we move the max(height[start], height[end]) we will be guaranteed that the volume will be lesser
//than the current volume. So lets try moving the min(height[start], height[end]) so we might get a shot at a larger volume 
//container. 

public class Solution {
	public int maxArea(int[] height) {
        int max = 0;
        int start = 0;
        int end = height.length-1;
        
        while(start < end) {
            int min = Math.min(height[start], height[end]);
            max = Math.max(max, min * (end-start));
            if (height[start] == height[end]) {
                ++start;
                --end;
            } else if (height[start] < height[end])
                ++start;
            else
                --end;
        }
        return max;
    }
}

```
