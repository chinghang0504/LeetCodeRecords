# [LeetCode Records](../../README.md) - Question 2130 Maximum Twin Sum of a Linked List

### Attempt 1: Use an int[] to save the node values
```java
class Solution {
    public int pairSum(ListNode head) {
        int[] nodes = new int[100001];
        int size = 0;

        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr.val;
            size++;
            curr = curr.next;
        }

        int maxSum = Integer.MIN_VALUE;
        for (int i = 0; i < size / 2; i++) {
            maxSum = Math.max(maxSum, nodes[i] + nodes[size - 1 - i]);
        }

        return maxSum;
    }
}
```
- Runtime: 5 ms (Beats: 69.28%)
- Memory: 55.52 MB (Beats: 99.84%)

<br>
