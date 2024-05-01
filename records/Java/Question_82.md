# [LeetCode Records](../../README.md) - Question 82 Remove Duplicates from Sorted List II

### Attempt 1: Use two pointers to save the nodes
```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy = new ListNode(0, head);
        ListNode curr1 = dummy;
        ListNode curr2 = head;

        while (curr2 != null) {
            int val = curr2.val;
            while (curr2.next != null && curr2.next.val == val) {
                curr2 = curr2.next;
            }
            if (curr1.next != curr2) {
                curr2 = curr2.next;
                curr1.next = curr2;
            } else {
                curr1 = curr2;
                curr2 = curr2.next;
            }
        }

        return dummy.next;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.62 MB (Beats: 10.94%)

<br>
