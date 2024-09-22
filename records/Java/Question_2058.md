# [LeetCode Records](../../README.md) - Question 2058 Find the Minimum and Maximum Number of Nodes Between Critical Points

### Attempt 1: Use an int[] to store the positions
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
    public int[] nodesBetweenCriticalPoints(ListNode head) {
        int[] positions = new int[100000];
        int size = 0;

        ListNode prev1 = head;
        ListNode prev2 = prev1.next;
        int position = 2;
        while (prev2.next != null) {
            int val1 = prev1.val;
            int val2 = prev2.val;
            int val3 = prev2.next.val;
            if ((val1 < val2 && val2 > val3) || (val1 > val2 && val2 < val3)) {
                positions[size] = position;
                size++;
            }

            prev1 = prev2;
            prev2 = prev2.next;
            position++;
        }

        if (size < 2) {
            return new int[]{ -1, -1 };
        }

        int minDistance = Integer.MAX_VALUE;
        for (int i = 1; i < size; i++) {
            minDistance = Math.min(minDistance, positions[i] - positions[i - 1]);
        }
        int maxDistance = positions[size - 1] - positions[0];

        return new int[]{ minDistance, maxDistance };
    }
}
```
- Runtime: 7 ms (Beats: 37.82%)
- Memory: 70.63 MB (Beats: 5.16%)

<br>
