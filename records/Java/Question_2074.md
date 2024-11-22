# [LeetCode Records](../../README.md) - Question 2074 Reverse Nodes in Even Length Groups

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
    public ListNode reverseEvenLengthGroups(ListNode head) {
        ListNode[] nodes = new ListNode[100000];
        int size = 0;
        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            size++;
            curr = curr.next;
        }

        int currLength = 1;
        int startIndex = 0;
        while (startIndex < size) {
            int endIndex = startIndex + currLength - 1;
            if (endIndex >= size) {
                endIndex = size - 1;
                currLength = size - startIndex;
            }

            if (currLength % 2 == 0) {
                for (int i = startIndex, j = endIndex; i < j; i++, j--) {
                    int val = nodes[i].val;
                    nodes[i].val = nodes[j].val;
                    nodes[j].val = val;
                }
            }

            startIndex += currLength;
            currLength++;
        }

        return nodes[0];
    }
}
```
- Runtime: 8 ms (Beats: 26.67%)
- Memory: 64.22 MB (Beats: 98.48%)

<br>
