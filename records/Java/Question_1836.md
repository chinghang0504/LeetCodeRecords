# [LeetCode Records](../../README.md) - Question 1836 Remove Duplicates From an Unsorted Linked List

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
    public ListNode deleteDuplicatesUnsorted(ListNode head) {
        ListNode[] nodes = new ListNode[100000];
        int size = 0;
        Map<Integer, Integer> map = new HashMap<>();

        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            map.merge(curr.val, 1, Integer::sum);

            size++;
            curr = curr.next;
        }

        for (int i = 0; i < size; i++) {
            if (map.get(nodes[i].val) > 1) {
                nodes[i] = null;
            }
        }

        ListNode dummy = new ListNode();
        curr = dummy;
        for (int i = 0; i < size; i++) {
            if (nodes[i] != null) {
                curr.next = nodes[i];
                curr = nodes[i];
            }
        }
        curr.next = null;

        return dummy.next;
    }
}
```
- Runtime: 63 ms (Beats: 85.96%)
- Memory: 67.18 MB (Beats: 10.53%)

<br>
