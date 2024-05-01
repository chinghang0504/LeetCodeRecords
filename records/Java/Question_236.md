# [LeetCode Records](../../README.md) - Question 236 Lowest Common Ancestor of a Binary Tree

### Attempt 1: Use recursion
```java
class Solution {

    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null) {
            return null;
        } else if (root == p || root == q) {
            return root;
        }

        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);

        if (left != null && right != null) {
            return root;
        } else if (left != null) {
            return left;
        } else {
            return right;
        }
    }
}
```
- Runtime: 6 ms (Beats: 100.00%)
- Memory: 44.30 MB (Beats: 93.20%)

<br>
