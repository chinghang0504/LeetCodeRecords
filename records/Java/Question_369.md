# [LeetCode Records](../../README.md) - Question 369 Plus One Linked List

### Attempt 1: Use an array to save the nodes first
```java
class Solution {
    public ListNode plusOne(ListNode head) {
        ListNode[] nodes = new ListNode[100];
        int count = 0;
        ListNode curr = head;

        while (curr != null) {
            nodes[count] = curr;
            curr = curr.next;
            count++;
        }
        
        boolean addOne = false;
        for (int i = count - 1; i >= 0; i--) {            
            int val = nodes[i].val + 1;
            if (val < 10) {
                nodes[i].val = val;
                addOne = false;
                break;
            } else {
                nodes[i].val = val - 10;
                addOne = true;
            }
        }

        return addOne ? new ListNode(1, head) : head;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.35 MB (Beats: 26.11%)

<br>
