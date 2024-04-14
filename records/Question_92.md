# [LeetCode Records](../README.md) - Question 92 Reverse Linked List II

### Attempt 1: Use an array to save the reversed nodes
```java
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        // Reverse one node
        if (left == right) {
            return head;
        }

        // Create a dummy head
        ListNode dummy = new ListNode(0, head);

        // Create an array to save the reversed nodes
        int size = right - left + 1;
        ListNode[] saved = new ListNode[size];

        // Get the node before the reversed nodes
        ListNode curr1 = dummy;
        for (int i = 0; i < left - 1; i++) {
            curr1 = curr1.next;
        }

        // Save the reversed nodes and get the node points to after the reversed node
        ListNode curr2 = curr1.next;
        for (int i = 0; i < size; i++) {
            saved[i] = curr2;
            curr2 = curr2.next;
        }

        // Connect the reversed nodes
        for (int i = size - 1; i >= 1; i--) {
            saved[i].next = saved[i - 1];
        }
        curr1.next = saved[size - 1];
        saved[0].next = curr2;

        return dummy.next;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.82 MB (Beats: 87.40%)

<br>
