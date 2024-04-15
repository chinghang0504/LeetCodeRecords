# [LeetCode Records](../README.md) - Question 147 Insertion Sort List

### Attempt 1: Use four ListNode to record the positions
```java
class Solution {
    public ListNode insertionSortList(ListNode head) {
        ListNode dummy = new ListNode(Integer.MIN_VALUE, head);
        ListNode curr1 = head.next;
        head.next = null;
        
        while (curr1 != null) {
            ListNode curr2 = dummy;
            ListNode curr3 = curr2.next;
            while (curr3 != null) {
                if (curr1.val < curr3.val) {
                    break;
                } else {
                    curr2 = curr3;
                    curr3 = curr3.next;
                }
            }
            curr2.next = curr1;
            curr1 = curr1.next;
            curr2.next.next = curr3;
        }

        return dummy.next;
    }
}
```
- Runtime: 18 ms (Beats: 53.37%)
- Memory: 44.68 MB (Beats: 18.89%)

<br>

### Attempt 2: Use an int array to record the nodes
```java
class Solution {
    public ListNode insertionSortList(ListNode head) {
        int[] saved = new int[10001];
        ListNode curr = head;
        while (curr != null) {
            saved[curr.val + 5000]++;
            curr = curr.next;
        }

        ListNode dummy = new ListNode();
        curr = dummy;
        for (int i = 0; i < 10001; i++) {
            if (saved[i] != 0) {
                for (int j = 0; j < saved[i]; j++) {
                    curr.next = new ListNode(i - 5000);
                    curr = curr.next;
                }
            }
        }

        return dummy.next;
    }
}
```
- Runtime: 1 ms (Beats: 99.88%)
- Memory: 44.54 MB (Beats: 28.83%)

<br>
