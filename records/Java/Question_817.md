# [LeetCode Records](../../README.md) - Question 817 Linked List Components

### Attempt 1: Use a HashSet the store the numbers and a boolean variable to track the linked list is connected or not
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
    public int numComponents(ListNode head, int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }

        boolean isConnected = false;
        int count = 0;
        ListNode curr = head;
        while (curr != null) {
            if (isConnected) {
                if (!set.contains(curr.val)) {
                    isConnected = false;
                }
            } else {
                if (set.contains(curr.val)) {
                    isConnected = true;
                    count++;
                }
            }

            curr = curr.next;
        }


        return count;
    }
}
```
- Runtime: 6 ms (Beats: 95.10%)
- Memory: 44.70 MB (Beats: 96.33%)

<br>
