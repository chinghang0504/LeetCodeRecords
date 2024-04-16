# [LeetCode Records](../README.md) - Question 445 Add Two Numbers II

### Attempt 1: Convert two lists into two arrays
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int[] num1 = new int[100];
        int size1 = 0;
        int[] num2 = new int[100];
        int size2 = 0;

        ListNode curr = l1;
        while (curr != null) {
            num1[size1++] = curr.val;
            curr = curr.next;
        }
        curr = l2;
        while (curr != null) {
            num2[size2++] = curr.val;
            curr = curr.next;
        }

        ListNode dummy = new ListNode(0);

        int minSize = Math.min(size1, size2);
        int plusOne = 0;
        int i = 0;
        for (; i < minSize; i++) {
            int val = num1[size1 - 1 - i] + num2[size2 - 1 - i] + plusOne;
            if (val > 9) {
                val -= 10;
                plusOne = 1;
            } else {
                plusOne = 0;
            }

            dummy.next = new ListNode(val, dummy.next);
        }
        for (; i < size1; i++) {
            int val = num1[size1 - 1 - i] + plusOne;
            if (val > 9) {
                val -= 10;
                plusOne = 1;
            } else {
                plusOne = 0;
            }

            dummy.next = new ListNode(val, dummy.next);
        }
        for (; i < size2; i++) {
            int val = num2[size2 - 1 - i] + plusOne;
            if (val > 9) {
                val -= 10;
                plusOne = 1;
            } else {
                plusOne = 0;
            }

            dummy.next = new ListNode(val, dummy.next);
        }
        if (plusOne == 1) {
            dummy.next = new ListNode(1, dummy.next);
        }

        return dummy.next;
    }
}
```
- Runtime: 2 ms (Beats: 56.55%)
- Memory: 44.82 MB (Beats: 9.02%)

<br>
