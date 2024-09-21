# [LeetCode Records](../../README.md) - Question 2674 Split a Circular Linked List

### Attempt 1: Use a ListNode[] to store nodes
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
    public ListNode[] splitCircularLinkedList(ListNode list) {
        ListNode[] nodes = new ListNode[100000];
        nodes[0] = list;

        ListNode curr = list.next;
        int size = 1;
        while (curr != list) {
            nodes[size] = curr;
            size++;
            curr = curr.next;
        }

        int nextHeadIndex = size % 2 == 0 ? size / 2 : size / 2 + 1;
        ListNode head1 = nodes[0];
        nodes[nextHeadIndex - 1].next = head1;

        ListNode head2 = nodes[nextHeadIndex];
        nodes[size - 1].next = head2;

        return new ListNode[]{ head1, head2 } ;
    }
}
```
- Runtime: 9 ms (Beats: 7.41%)
- Memory: 65.16 MB (Beats: 54.32%)

<br>
