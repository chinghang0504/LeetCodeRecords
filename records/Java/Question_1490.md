# [LeetCode Records](../../README.md) - Question 1490 Clone N-ary Tree

### Attempt 1: Use recursion
```java
class Solution {
    public Node cloneTree(Node root) {
        if (root == null) {
            return null;
        }

        Node copyRoot = new Node(root.val);
        cloneTreeRecursion(root, copyRoot);

        return copyRoot;
    }

    private void cloneTreeRecursion(Node root, Node copyRoot) {
        for (Node childNode : root.children) {
            Node node = new Node(childNode.val);
            copyRoot.children.add(node);
            cloneTreeRecursion(childNode, node);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 46.43 MB (Beats: 84.66%)

<br>
