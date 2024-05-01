# [LeetCode Records](../../README.md) - Question 19 Remove Nth Node From End of List

### Attempt 1: Count the size first
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        int count = 0;
        ListNode curr = head;
        while (curr != null) {
            count++;
            curr = curr.next;
        }

        int moveTimes = count - n - 1;
        if (moveTimes == -1) {
            return head.next;
        }

        curr = head;
        for (int i = 0; i < moveTimes; i++) {
            curr = curr.next;
        }
        curr.next = curr.next.next;

        return head;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.10 MB (Beats: 7.41%)

<br>
