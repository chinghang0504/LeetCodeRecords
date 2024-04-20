# [LeetCode Records](../README.md) - Question 148 Sort List

### Attempt 1: Use an int array to record numbers
```java
class Solution {

    public ListNode sortList(ListNode head) {
        int[] saved = new int[200001];
        ListNode curr = head;
        while (curr != null) {
            saved[curr.val + 100000]++;
            curr = curr.next;
        }

        ListNode dummy = new ListNode();
        curr = dummy;
        for (int i = 0; i < 200001; i++) {
            while (saved[i] > 0) {
                curr.next = new ListNode(i - 100000);
                curr = curr.next;
                saved[i]--;
            }
        }

        return dummy.next;
    }
}
```
- Runtime: 11 ms (Beats: 42.15%)
- Memory: 54.78 MB (Beats: 96.96%)

<br>
