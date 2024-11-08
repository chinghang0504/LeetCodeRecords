# [LeetCode Records](../../README.md) - Question 1019 Next Greater Node In Linked List

### Attempt 1: Use a PriorityQueue to store the value and its index
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
    public int[] nextLargerNodes(ListNode head) {
        int[] maxVals = new int[10000];
        PriorityQueue<int[]> priorityQueue = new PriorityQueue<>((item1, item2) -> item1[0] - item2[0]);

        int size = 0;
        ListNode curr = head;
        while (curr != null) {
            int[] item = priorityQueue.peek();
            while (item != null && curr.val > item[0]) {
                maxVals[item[1]] = curr.val;
                priorityQueue.poll();
                item = priorityQueue.peek();
            }

            priorityQueue.add(new int[]{ curr.val, size });
            size++;
            curr = curr.next;
        }
        
        return Arrays.copyOf(maxVals, size);
    }
}
```
- Runtime: 21 ms (Beats: 86.49%)
- Memory: 47.53 MB (Beats: 46.46%)

<br>
