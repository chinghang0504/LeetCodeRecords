# [LeetCode Records](../README.md) - Question 142 Linked List Cycle II

### Attempt 1: Use a HashSet to record viewed ListNode
```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        HashSet<ListNode> saved = new HashSet<>();
        ListNode curr = head;

        while (curr != null) {
            if (saved.contains(curr)) {
                return curr;
            } else {
                saved.add(curr);
                curr = curr.next;
            }
        }

        return null;
    }
}
```
- Runtime: 3 ms (Beats: 15.00%)
- Memory: 44.65 MB (Beats: 21.11%)

<br>
