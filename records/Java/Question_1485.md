# [LeetCode Records](../../README.md) - Question 1485 Clone Binary Tree With Random Pointer

### Attempt 1: Use a HashMap to store the node and the copy of node key-value pairs
```java
/**
 * Definition for Node.
 * public class Node {
 *     int val;
 *     Node left;
 *     Node right;
 *     Node random;
 *     Node() {}
 *     Node(int val) { this.val = val; }
 *     Node(int val, Node left, Node right, Node random) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *         this.random = random;
 *     }
 * }
 */

class Solution {

    private Map<Node, NodeCopy> map;

    public NodeCopy copyRandomBinaryTree(Node root) {
        map = new HashMap<>();

        NodeCopy rootCopy = copyNodeRecursion(root);
        setRandomPointerRecursion(root, rootCopy);

        return rootCopy;
    }

    private NodeCopy copyNodeRecursion(Node root) {
        if (root == null) {
            return null;
        }

        NodeCopy rootCopy = new NodeCopy(root.val);
        map.put(root, rootCopy);

        rootCopy.left = copyNodeRecursion(root.left);
        rootCopy.right = copyNodeRecursion(root.right);

        return rootCopy;
    }

    private void setRandomPointerRecursion(Node root, NodeCopy rootCopy) {
        if (root == null) {
            return;
        }

        Node randomNode = root.random;
        if (randomNode != null) {
            rootCopy.random = map.get(randomNode);
        }

        setRandomPointerRecursion(root.left, rootCopy.left);
        setRandomPointerRecursion(root.right, rootCopy.right);
    }
}
```
- Runtime: 4 ms (Beats: 100.00%)
- Memory: 45.22 MB (Beats: 95.54%)

<br>
