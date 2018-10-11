## Problem
Implement atoi which converts a string to an integer.

Discard any white spaces. Takes an optional +/- sign followed by any number of numberic digits
## Solution


```Java
//idea: skip all white spaces untill you see a number/plus/minus. Mark that as the begining of your number
// accumulate the result into a long to account for integer overflow. 
public class Solution {
	public int myAtoi(String str) {
        long res = 0;
        boolean numberStart = false;
        int sign = 1;
        
        for(int i=0; i<str.length(); ++i) {
            char c = str.charAt(i);
            if (c == ' ' && (!numberStart))
                continue;
            
            if (c < '0' || c > '9') {
                if ((!numberStart) && (c == '+' || c == '-')) {
                    numberStart = true;
                    sign = c == '-' ? -1 : 1;
                    continue;
                } else {
                    return (int) res;
                }
            } else {
                numberStart = true;
            }
            res = res*10 + ((c-'0')*sign);
            
            if (res > Integer.MAX_VALUE)
                return Integer.MAX_VALUE;
            if (res < Integer.MIN_VALUE)
                return Integer.MIN_VALUE;
        }
        return (int) res;
    }
}
