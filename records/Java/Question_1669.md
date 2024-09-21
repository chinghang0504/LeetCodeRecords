# [LeetCode Records](../../README.md) - Question 1669 Merge In Between Linked Lists

### Attempt 1: Save the nodes list1tail1, list1tail2, and list2tail1
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
    public ListNode mergeInBetween(ListNode list1, int a, int b, ListNode list2) {
        int step = a - 1;
        ListNode list1Tail1 = list1;
        for (int i = 0; i < step; i++) {
            list1Tail1 = list1Tail1.next;
        }

        step = b - a + 2;
        ListNode list1Tail2 = list1Tail1;
        for (int i = 0; i < step; i++) {
            list1Tail2 = list1Tail2.next;
        }

        ListNode list2Tail1 = list2;
        while (list2Tail1.next != null) {
            list2Tail1 = list2Tail1.next;
        }

        list1Tail1.next = list2;
        list2Tail1.next = list1Tail2;
        return list1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 46.22 MB (Beats: 69.79%)

<br>
