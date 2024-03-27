# [LeetCode Records](../README.md) - Question 24 Swap Nodes in Pairs

### Attempt 1: Use a dummy head
```java
class Solution {
    public ListNode swapPairs(ListNode head) {
        if (head == null) {
            return null;
        }
        
        ListNode dummy = new ListNode();
        dummy.next = head;
        ListNode curr = dummy;
        while (curr.next != null && curr.next.next != null) {
            ListNode first = curr.next;
            ListNode second = curr.next.next;
            first.next = second.next;
            second.next = first;
            curr.next = second;
            curr = first;
        }
        
        return dummy.next;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.18 MB (Beats: 52.46%)

<br>
