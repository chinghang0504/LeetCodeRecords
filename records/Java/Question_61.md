# [LeetCode Records](../../README.md) - Question 61 Rotate List

### Attempt 1: Calculate the number of nodes first
```java
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        // Empty head
        if (head == null) {
            return null;
        }

        int count = 0;
        ListNode curr = head;

        // Count the number of nodes
        while (curr.next != null) {
            count++;
            curr = curr.next;
        }
        count++;

        // Calculate the new k
        int newK = k % count;

        // Do not need to rotate
        if (newK == 0) {
            return head;
        }

        // Connect the tail to the head
        curr.next = head;

        // Calculate the move
        int move = count - newK - 1;
        curr = head;
        for(int i = 0; i < move; i++) {
            curr = curr.next;
        }
        
        // Get the new head
        ListNode newHead = curr.next;
        curr.next = null;

        return newHead;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.56 MB (Beats: 34.90%)

<br>
