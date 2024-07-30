# [LeetCode Records](../../README.md) - Question 1474 Delete N Nodes After M Nodes of a Linked List

### Attempt 1: Use a ListNode[] to save the nodes
```java
class Solution {
    public ListNode deleteNodes(ListNode head, int m, int n) {
        ListNode[] saved = new ListNode[10000];
        int size = 0;

        ListNode curr = head;
        while (curr != null) {
            saved[size] = curr;
            curr = curr.next;
            size++;
        }

        int step = m + n;
        for (int i = m - 1; i < size; i += step) {
            int nextIndex = i + n + 1;
            saved[i].next = nextIndex < size ? saved[nextIndex] : null;
        }

        return head;
    }
}
```
- Runtime: 1 ms (Beats: 94.38%)
- Memory: 44.56 MB (Beats: 84.83%)

<br>
