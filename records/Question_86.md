# [LeetCode Records](../README.md) - Question 86 Partition List

### Attempt 1: Use three pointers
```java
class Solution {
    public ListNode partition(ListNode head, int x) {
        ListNode dummy1 = new ListNode(0, head);
        ListNode curr1 = dummy1;
        ListNode curr2 = head;

        ListNode dummyLess = new ListNode();
        ListNode currLess = dummyLess;
        
        while (curr2 != null) {
            if (curr2.val < x) {
                currLess.next = curr2;
                currLess = curr2;
                curr1.next = curr2.next;
                curr2 = curr2.next;
            } else {
                curr1 = curr2;
                curr2 = curr2.next;
            }
        }

        currLess.next = dummy1.next;
        return dummyLess.next;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.74 MB (Beats: 78.14%)

<br>
