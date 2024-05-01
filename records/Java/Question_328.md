# [LeetCode Records](../../README.md) - Question 328 Odd Even Linked List

### Attempt 1: Use three pointers to reocrd the current nodes
```java
class Solution {
    public ListNode oddEvenList(ListNode head) {
        ListNode dummyOdd = new ListNode(0, head);
        ListNode curr1 = dummyOdd;
        ListNode curr2 = head;

        ListNode dummyEven = new ListNode(0);
        ListNode currEven = dummyEven;

        boolean isOdd = true;
        while (curr2 != null) {
            if (!isOdd) {
                currEven.next = curr2;
                currEven = curr2;
                curr2 = curr2.next;
                curr1.next = curr2;
            } else {
                curr1 = curr2;
                curr2 = curr2.next;
            }

            isOdd = !isOdd;
        }

        curr1.next = dummyEven.next;
        currEven.next = null;
        return dummyOdd.next;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.78 MB (Beats: 14.25%)

<br>
