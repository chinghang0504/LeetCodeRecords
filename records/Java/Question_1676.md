# [LeetCode Records](../../README.md) - Question 1676 Lowest Common Ancestor of a Binary Tree IV

### Attempt 1: Use a HashSet to store the target nodes
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {

    private Set<TreeNode> targetNodes;

    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode[] nodes) {
        targetNodes = new HashSet<>();
        for (TreeNode node : nodes) {
            targetNodes.add(node);
        }

        return lowestCommonAncestorRecursion(root);
    }

    private TreeNode lowestCommonAncestorRecursion(TreeNode root) {
        if (root == null) {
            return null;
        } else if (targetNodes.contains(root)) {
            return root;
        }

        TreeNode left = lowestCommonAncestorRecursion(root.left);
        TreeNode right = lowestCommonAncestorRecursion(root.right);
        if (left != null && right != null) {
            return root;
        } else if (left != null) {
            return left;
        } else if (right != null) {
            return right;
        } else {
            return null;
        }
    }
}
```
- Runtime: 3 ms (Beats: 77.05%)
- Memory: 45.40 MB (Beats: 79.90%)

<br>

### Attempt 1: Search the target node in the TreeNode[]
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {

    private Set<TreeNode> targetNodes;

    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode[] nodes) {
        if (root == null) {
            return null;
        }

        for (TreeNode node : nodes) {
            if (node == root) {
                return root;
            }
        }

        TreeNode left = lowestCommonAncestor(root.left, nodes);
        TreeNode right = lowestCommonAncestor(root.right, nodes);
        if (left != null && right != null) {
            return root;
        } else if (left != null) {
            return left;
        } else if (right != null) {
            return right;
        } else {
            return null;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.96 MB (Beats: 45.06%)

<br>
