# [LeetCode Records](../README.md) - Question 25 Reverse Nodes in k-Group

### Attempt 1: Use a ListNode array to save nodes for reversing
```java
class Solution {
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode[] saved = new ListNode[k];
        ListNode curr1 = head;
        ListNode curr2 = null;

        loop: while (true) {
            // Save the nodes
            for (int i = 0; i < k; i++) {
                // Not enough of nodes
                if (curr1 == null) break loop;
                saved[i] = curr1;
                curr1 = curr1.next;
            }

            // Save the new head
            if (curr2 == null) {
                head = saved[k - 1];
            } else {
                curr2.next = saved[k - 1];
            }

            // Reverse the nodes
            curr2 = saved[k - 1];
            for (int i = k - 2; i >= 0; i--) {
                curr2.next = saved[i];
                curr2 = saved[i];
            }
            curr2.next = curr1;
        }
        
        return head;
    }
}
```
- Runtime: 1 ms (Beats: 31.77%)
- Memory: 44.28 MB (Beats: 42.50%)

<br>
