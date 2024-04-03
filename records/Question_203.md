# [LeetCode Records](../README.md) - Question 203 Remove Linked List Elements

### Attempt 1: Check from the second node
```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode curr = head;
        if (curr == null) {
            return null;
        }

        while (curr.next != null) {
            if (curr.next.val == val) {
                curr.next = curr.next.next;
            } else {
                curr = curr.next;
            }
        }

        if (head.val == val) {
            return head.next;
        } else {
            return head;
        }
    }
}
```
- Runtime: 1 ms (Beats: 93.05%)
- Memory: 45.60 MB (Beats: 36.20%)

<br>
