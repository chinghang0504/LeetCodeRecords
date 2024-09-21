# [LeetCode Records](../../README.md) - Question 2095 Delete the Middle Node of a Linked List

### Attempt 1: Find the number of nodes first
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
    public ListNode deleteMiddle(ListNode head) {
        int size = 0;
        ListNode curr = head;
        while (curr != null) {
            size++;
            curr = curr.next;
        }

        if (size == 1) {
            return null;
        }

        int step = size / 2 - 1;
        curr = head;
        for (int i = 0; i < step; i++) {
            curr = curr.next;
        }

        curr.next = curr.next.next;
        return head;
    }
}
```
- Runtime: 3 ms (Beats: 99.78%)
- Memory: 62.96 MB (Beats: 81.15%)

<br>
