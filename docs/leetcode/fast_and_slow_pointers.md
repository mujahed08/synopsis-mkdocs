# Fast & Slow Pointers

## Linked List Cycle

[leetcode.com/problems/linked-list-cycle/description/](https://leetcode.com/problems/linked-list-cycle/description/)

Easy

```java

/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast) {
                return true;
            }
        }

        return false;
    }
}

```

## Happy Number

[https://leetcode.com/happy-number](https://leetcode.com/problems/happy-number/description/)

Easy

```java

class Solution {
    public boolean isHappy(int n) {
        
        int slow = n;
        int fast = sumOfSquareOfDigits(n);

        while(slow != fast) {
            slow = sumOfSquareOfDigits(slow);
            fast = sumOfSquareOfDigits(sumOfSquareOfDigits(fast));
        }
        
        return slow == 1;
    }

    public int sumOfSquareOfDigits(int n){
        
        int sum = 0; 
        while(n > 0 ){
            int reminder = n % 10;
            sum += (reminder * reminder);
            n = n / 10; // reverses the given number
        }
        return sum;
    }
}

```