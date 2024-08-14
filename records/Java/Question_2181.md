# [LeetCode Records](../../README.md) - Question 2181 Merge Nodes in Between Zeros

### Attempt 1: Create a new node for each local sum
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
    public ListNode mergeNodes(ListNode head) {
        ListNode dummy = new ListNode();
        ListNode ansCurr = dummy;

        ListNode curr = head;
        while (curr.next != null) {
            curr = curr.next;

            int sum = 0;
            while (curr.val != 0) {
                sum += curr.val;
                curr = curr.next;
            }

            ansCurr.next = new ListNode(sum);
            ansCurr = ansCurr.next;
        }

        return dummy.next;
    }
}
```
- Runtime: 5 ms (Beats: 67.54%)
- Memory: 81.11 MB (Beats: 75.64%)

<br>
