# [LeetCode Records](../../README.md) - Question 206 Reverse Linked List

### Attempt 1: Use two ListNode
```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;

        while (curr != null) {
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        return prev;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.05 MB (Beats: 86.40%)

<br>
