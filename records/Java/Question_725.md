# [LeetCode Records](../../README.md) - Question 725 Split Linked List in Parts

### Attempt 1: Use a ListNode[] to store the nodes
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
    public ListNode[] splitListToParts(ListNode head, int k) {
        ListNode[] nodes = new ListNode[1000];
        int size = 0;
        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            size++;
            curr = curr.next;
        }

        int average = size / k;
        int[] sizes = new int[k];
        for (int i = 0; i < k; i++) {
            sizes[i] = average;
        }
        int remainingSize = size - average * k;
        int sizeIndex = 0;
        while (remainingSize > 0) {
            sizes[sizeIndex]++;
            sizeIndex++;
            remainingSize--;
        }

        ListNode[] ans = new ListNode[k];
        int start = 0;
        for (int i = 0; i < k; i++) {
            int currSize = sizes[i];
            if (currSize == 0) {
                break;
            }

            ans[i] = nodes[start];
            start += currSize;
            nodes[start - 1].next = null;
        }

        return ans;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.30 MB (Beats: 65.85%)

<br>
