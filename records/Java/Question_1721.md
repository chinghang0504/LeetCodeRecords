# [LeetCode Records](../../README.md) - Question 1721 Swapping Nodes in a Linked List

### Attempt 1: Use a ListNode[] to store nodes
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 * int val;
 * ListNode next;
 * ListNode() {}
 * ListNode(int val) { this.val = val; }
 * ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode swapNodes(ListNode head, int k) {
        ListNode[] nodes = new ListNode[100000];
        int size = 0;
        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            size++;
            curr = curr.next;
        }

        int start = k - 1;
        int end = size - k;

        if (start != end) {
            int temp = nodes[start].val;
            nodes[start].val = nodes[end].val;
            nodes[end].val = temp;
        }

        return nodes[0];
    }
}
```
- Runtime: 4 ms (Beats: 14.21%)
- Memory: 57.58 MB (Beats: 99.31%)

<br>
