# [LeetCode Records](../../README.md) - Question 237 Delete Node in a Linked List

### Attempt 1: 
```java
class Solution {
    public void deleteNode(ListNode node) {
        if (node == null) {
            return;
        }

        ListNode curr = node;
        while (curr.next != null && curr.next.next != null) {
            curr.val = curr.next.val;
            curr = curr.next;
        }
        curr.val = curr.next.val;
        curr.next = null;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.87 MB (Beats: 48.61%)

<br>
