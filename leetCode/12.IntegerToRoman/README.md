## Problem


## Solution

```Java

class Solution {
    //idea: divide the int by great roman numeral that gives a positive dividend. 
    public String intToRoman(int num) {
        StringBuilder sb = new StringBuilder();
        String[] romans = new String[]{
            "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int[] nums = new int[]{
            1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        
        int i=0;
        while(i < nums.length && num > 0) {
            int c = num/nums[i];
            if (c > 0) {
                while(c-- > 0) {
                    sb.append(romans[i]);
                }
                num = num % nums[i];
            }
            i++;
        }
        return sb.toString();
    }
}
```
