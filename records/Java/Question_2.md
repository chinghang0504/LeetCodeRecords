# [LeetCode Records](../../README.md) - Question 2 Add Two Numbers

### Attempt 1: Loop the elements of l1 and l2 at the same time
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = null;
        ListNode curr = head;
        int plusOne = 0;

        while (l1 != null || l2 != null) {
            int val = plusOne;
            if (l1 != null) {
                val += l1.val;
            }
            if (l2 != null) {
                val += l2.val;
            }

            if (val >= 10) {
                val -= 10;
                plusOne = 1;
            } else {
                plusOne = 0;
            }

            ListNode newNode = new ListNode(val);
            if (head != null) {
                curr.next = newNode;
                curr = curr.next;
            } else {
                head = newNode;
                curr = head;
            }

            if (l1 != null) {
                l1 = l1.next;
            }
            if (l2 != null) {
                l2 = l2.next;
            }
        }

        if (plusOne == 1) {
            curr.next = new ListNode(1);
        }

        return head;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.00 MB (Beats: 94.65%)

<br>

### Attempt 2: Remove redundant code
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = new ListNode();
        ListNode curr = head;
        boolean plusOne = false;

        while (l1 != null || l2 != null || plusOne) {
            int val = plusOne ? 1 : 0;

            if (l1 != null) {
                val += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                val += l2.val;
                l2 = l2.next;
            }

            if (val >= 10) {
                plusOne = true;
                curr.next = new ListNode(val - 10);
            } else {
                plusOne = false;
                curr.next = new ListNode(val);
            }

            curr = curr.next;
        }

        return head.next;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.41 MB (Beats: 41.73%)

<br>
