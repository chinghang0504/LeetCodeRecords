# [LeetCode Records](../../README.md) - Question 2487 Remove Nodes From Linked List

### Attempt 1: Use a ListNode[] to store the nodes
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNodes(ListNode head) {
        ListNode[] nodes = new ListNode[100000];
        int size = 0;
        
        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            curr = curr.next;
            size++;
        }

        ListNode tail = nodes[size - 1];
        for (int i = size - 2; i >= 0; i--) {
            ListNode beforeTail = nodes[i];
            if (beforeTail.val >= tail.val) {
                beforeTail.next = tail;
                tail = beforeTail;
            }
        }

        return tail;
    }
}
```
- Runtime: 5 ms (Beats: 94.61%)
- Memory: 63.94 MB (Beats: 74.30%)

<br>
