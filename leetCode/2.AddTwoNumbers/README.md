##Problem

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.:1


##Solution

```java
/**
*  public class ListNode {
*  	int val;
*	ListNode next;
*  }
*/
public class Solution {
	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
		//digits are stored in reverse order. ex. (tail)1<-2<-3(head)  for number 123
		//add the two lists till either one is done. save the carry if there is any
		ListNode result = null;
		ListNode start = null;
		int carry = 0;
		while(l1 !=null || l2 != null || carry != 0) {
			int sum = (l1 != null ? l1.val : 0) + (l2 != null ? l2.val : 0) + carry;
			if (result == null) {
				result = new ListNode(sum%10);
				start = result;
			} else {
				result.next = new ListNode(sum%10);
				result = result.next;
			}
			if (l1 != null)
				l1 = l1.next;
			if (l2 != null)
				l2 = l2.next;
			carry = sum/10;
		}
		
		return start;
	}
}


//Accepted recursive solution
public class Solution {
	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
		ListNode res = new ListNode(0);
		recursiveAdd(l1, l2, 0, res);
		return res.next;
	}

	private ListNode recursiveAdd(ListNode l1, ListNode l2, int carry, ListNode result) {
		if (l1 == null && l2 == null && carry == 0) 
			return result;
		
		int sum = 0;
		if (l1 != null) {
			sum+= l1.val;
			l1 = l1.next;
		}
		if (l2 != null) {
			sum+= l2.val;
			l2 = l2.next;
		}
		sum += carry;
		result.next = new ListNode(sum%10);
		result = result.next;
		return recursiveAdd(l1, l2, sum/10, result);	
	}
}

```
