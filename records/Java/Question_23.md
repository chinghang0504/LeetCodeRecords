# [LeetCode Records](../../README.md) - Question 23 Merge k Sorted Lists

### Attempt 1: Loop for checking each list
```java
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        ListNode head = new ListNode();
        ListNode curr = head;

        while (true) {
            int minValue = Integer.MAX_VALUE;
            int minIndex = -1;
            for (int i = 0; i < lists.length; i++) {
                if (lists[i] != null && lists[i].val < minValue) {
                    minValue = lists[i].val;
                    minIndex = i;
                }
            }
            if (minIndex != -1) {
                ListNode node = new ListNode(minValue);
                curr.next = node;
                curr = node;
                lists[minIndex] = lists[minIndex].next;
            } else {
                break;
            }
        }

        return head.next;
    }
}
```
- Runtime: 130 ms (Beats: 8.10%)
- Memory: 44.60 MB (Beats: 22.12%)

<br>
