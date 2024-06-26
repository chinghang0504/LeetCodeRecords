# [LeetCode Records](../../README.md) - Question 3063 Linked List Frequency

### Attempt 1: Use a HashMap to count the frequency of each number
```java
class Solution {
    public ListNode frequenciesOfElements(ListNode head) {
        Map<Integer, Integer> map = new HashMap<>();

        ListNode curr = head;
        while (curr != null) {
            map.merge(curr.val, 1, Integer::sum);
            curr = curr.next;
        }

        ListNode dummy = new ListNode();
        curr = dummy;
        for (Integer item : map.values()) {
            curr.next = new ListNode(item);
            curr = curr.next;
        }

        return dummy.next;
    }
}
```
- Runtime: 31 ms (Beats: 76.42%)
- Memory: 56.06 MB (Beats: 89.84%)

<br>
