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

        while(fast != 1 && slow != fast) {
            slow = getNextNumber(slow);
            fast = getNextNumber(getNextNumber(fast));
        }
        
        return fast == 1;
    }

    public int getNextNumber(int n){
        
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

## Find the Duplicate Number

[https://leetcode.com//find-the-duplicate-number](https://leetcode.com/problems/find-the-duplicate-number/description/)

Medium

```java
class Solution {
    public int findDuplicate(int[] nums) {
        
        int slow = nums[0];
        int fast = nums[0];

        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while(slow != fast);
        
        slow = nums[0];
        while(slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }

        return fast;
    }
}
```