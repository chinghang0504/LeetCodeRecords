# [LeetCode Records](../../README.md) - Question 141 Linked List Cycle

### Attempt 1: Use a HashMap
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        HashMap<ListNode, Integer> hashMap = new HashMap<>();

        ListNode curr = head;
        while (curr != null) {
            Integer saved = hashMap.get(curr);
            if (saved != null) {
                return true;
            } else {
                hashMap.put(curr, 0);
                curr = curr.next;
            }
        }

        return false;
    }
}
```
- Runtime: 6 ms (Beats: 9.04%)
- Memory: 44.98 MB (Beats: 6.48%)

<br>

### Attempt 2: Use a slow node and a fast node
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null) {
            return false;
        }

        ListNode slow = head;
        ListNode fast = head.next;

        while (true) {
            if (slow == fast) {
                return true;
            }

            if (slow == null) {
                break;
            }
            slow = slow.next;

            if (fast == null || fast.next == null) {
                break;
            }
            fast = fast.next.next;
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.14 MB (Beats: 72.82%)

<br>
