# [LeetCode Records](../../README.md) - Question 3294 Convert Doubly Linked List to Array II

### Attempt 1: Use a LinkedList to store the numbers
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node prev;
    public Node next;
};
*/

class Solution {
    public int[] toArray(Node node) {
        List<Integer> list = new LinkedList<>();

        Node curr = node.prev;
        while (curr != null) {
            list.addFirst(curr.val);
            curr = curr.prev;
        }

        curr = node;
        while (curr != null) {
            list.addLast(curr.val);
            curr = curr.next;
        }

        int[] ans = new int[list.size()];
        int i = 0;
        for (int num : list) {
            ans[i] = num;
            i++;
        }

        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 47.06%)
- Memory: 45.38 MB (Beats: 52.94%)

<br>
