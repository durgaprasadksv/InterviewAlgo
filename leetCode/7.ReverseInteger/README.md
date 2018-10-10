## Problem

Given a 32-bit signed integer, reverse digits of an integer.


## Solution

```Java
public class Solution {
	//idea is to use a long to carry the reverse of the integer. This can help us deal with overflow cases
	public int reverse(int x) {
		long rev = 0;
		while (x!=0) {
			rev = rev*10 + x%10;
			if (rev < Integer.MIN_VALUE || rev > Integer.MAX_VALUE) 
				return 0;	
			x = x/10;
		}
		return (int) rev;
	}

	//we can also do this without using a long and overflow checks
	public int reverse(int x) {
		int rev = 0;
		while(x != 0) {
			int t = x%10;
			int n = rev*10 + t;
			if (((n-t)/10) != rev) 
				return 0;
			rev = n;
			x = x/10;
		}
	}
}

```


