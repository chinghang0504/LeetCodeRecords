# [LeetCode Records](../../README.md) - Question 430 Flatten a Multilevel Doubly Linked List

### Attempt 1: Use recursion that returns the tail of a list
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node prev;
    public Node next;
    public Node child;
};
*/

class Solution {
    public Node flatten(Node head) {
        if (head == null) {
            return null;
        }

        flattenRecursion(head);
        return head;
    }

    private Node flattenRecursion(Node head) {
        Node curr = head;
        while (curr.next != null) {
            if (curr.child != null) {
                Node nextNode = curr.next;
                Node childHeadNode = curr.child;
                Node childTailNode = flattenRecursion(childHeadNode);
                curr.next = childHeadNode;
                childHeadNode.prev = curr;
                childTailNode.next = nextNode;
                nextNode.prev = childTailNode;
                curr.child = null;
            }

            curr = curr.next;
        }

        if (curr.child == null) {
            return curr;
        }

        Node childHeadNode = curr.child;
        Node childTailNode = flattenRecursion(childHeadNode);
        curr.next = childHeadNode;
        childHeadNode.prev = curr;
        curr.child = null;

        return childTailNode;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.60 MB (Beats: 44.77%)

<br>
