# [LeetCode Records](../../README.md) - Question 3217 Delete Nodes From Linked List Present in Array

### Attempt 1: Use a HashSet to store the removed numbers
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
    public ListNode modifiedList(int[] nums, ListNode head) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }

        ListNode dummy = new ListNode();
        ListNode nextListCurr = dummy;
        ListNode prevListCurr = head;
        while (prevListCurr != null) {
            if (!set.contains(prevListCurr.val)) {
                nextListCurr.next = prevListCurr;
                nextListCurr = prevListCurr;
            }

            prevListCurr = prevListCurr.next;
        }
        nextListCurr.next = null;

        return dummy.next;
    }
}
```
- Runtime: 20 ms (Beats: 76.27%)
- Memory: 66.44 MB (Beats: 24.61%)

<br>
