# [LeetCode Records](../../README.md) - Question 876 Middle of the Linked List

### Attempt 1: Count the number of nodes first
```java
class Solution {
    public ListNode middleNode(ListNode head) {
        int count = 0;
        ListNode curr = head;
        while (curr != null) {
            count++;
            curr = curr.next;
        }

        int middle = count / 2;
        curr = head;
        for (int i = 0; i < middle; i++) {
            curr = curr.next;
        }

        return curr;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.74 MB (Beats: 77.17%)

<br>
