# [LeetCode Records](../../README.md) - Question 426 Convert Binary Search Tree to Sorted Doubly Linked List

### Attempt 1: Use recursion to get the nodes in order
```java
class Solution {

    private Node curr;

    public Node treeToDoublyList(Node root) {
        if (root == null) {
            return null;
        }

        Node dummy = new Node();
        curr = dummy;

        treeToDoublyListRecursion(root);

        Node head = dummy.right;
        head.left = curr;
        curr.right = head;

        return head;
    }

    private void treeToDoublyListRecursion(Node root) {
        if (root == null) {
            return;
        }

        treeToDoublyListRecursion(root.left);

        curr.right = root;
        root.left = curr;
        curr = root;

        treeToDoublyListRecursion(root.right);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.44 MB (Beats: 94.76%)

<br>
