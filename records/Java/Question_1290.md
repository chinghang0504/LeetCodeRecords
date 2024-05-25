# [LeetCode Records](../../README.md) - Question 1290 Convert Binary Number in a Linked List to Integer

### Attempt 1: Use an int[]
```java
class Solution {
    public int getDecimalValue(ListNode head) {
        int[] nodes = new int[30];
        int count = 0;

        ListNode curr = head;
        while (curr != null) {
            nodes[count] = curr.val;
            count++;
            curr = curr.next;
        }

        int sum = 0;
        int multiplier = 1;
        for (int i = count - 1; i >= 0; i--) {
            sum += nodes[i] * multiplier;
            multiplier *= 2;
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.51 MB (Beats: 6.87%)

<br>
