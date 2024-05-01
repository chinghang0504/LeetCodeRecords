# [LeetCode Records](../../README.md) - Question 80 Remove Duplicates from Sorted List

### Attempt 1: Stay on the current node and check the next node
```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) {
            return null;
        }

        ListNode curr = head;

        while (curr.next != null) {
            if (curr.val == curr.next.val) {
                curr.next = curr.next.next;
            } else {
                curr = curr.next;
            }
        }
        
        return head;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.03 MB (Beats: 41.82%)

<br>
