# [LeetCode Records](../README.md) - Question 143 Reorder List

### Attempt 1: Use an array to save nodes
```java
class Solution {
    public void reorderList(ListNode head) {
        // Count the number of nodes
        ListNode dummy = new ListNode(0, head);
        ListNode curr = head;
        int size = 0;
        for (; curr != null; size++) {
            curr = curr.next;
        }

        // Save each node
        ListNode[] saved = new ListNode[size];
        curr = dummy;
        for (int i = 0; i < size; i++) {
            saved[i] = curr.next;
            curr = curr.next;
        }

        // Connect all nodes
        curr = dummy;
        int j = 0;
        for (int i = 0; i < size; i++) {
            if (i % 2 == 0) {
                curr.next = saved[j];
            } else {
                curr.next = saved[size - j - 1];
                j++;
            }
            curr = curr.next;
        }

        curr.next = null;
    }
}
```
- Runtime: 1 ms (Beats: 99.85%)
- Memory: 48.13 MB (Beats: 56.26%)

<br>
