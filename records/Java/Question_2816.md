# [LeetCode Records](../../README.md) - Question 2816 Double a Number Represented as a Linked List

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
    public ListNode doubleIt(ListNode head) {
        ListNode[] nodes = new ListNode[10000];
        int size = 0;

        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            size++;
            curr = curr.next;
        }

        int plusOne = 0;
        for (int i = size - 1; i >= 0; i--) {
            int val = nodes[i].val * 2 + plusOne;
            if (val >= 10) {
                val -= 10;
                plusOne = 1;
            } else {
                plusOne = 0;
            }
            nodes[i].val = val;
        }

        return plusOne == 0 ? head : new ListNode(plusOne, head);
    }
}
```
- Runtime: 6 ms (Beats: 31.79%)
- Memory: 46.05 MB (Beats: 67.56%)

<br>
