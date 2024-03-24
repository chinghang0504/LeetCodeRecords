# [LeetCode Records](../README.md) - Question 21 Merge Two Sorted Lists

### Attempt 1: Read nodes at the same time
```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode head = new ListNode();
        ListNode curr = head;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                curr.next = list1;
                list1 = list1.next;
            } else {
                curr.next = list2;
                list2 = list2.next;
            }

            curr = curr.next;
        }

        if (list1 != null) {
            curr.next = list1;
        } else {
            curr.next = list2;
        }

        return head.next;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.46 MB (Beats: 44.80%)

<br>
