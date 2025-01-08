# [LeetCode Records](../../README.md) - Question 814 Binary Tree Pruning

### Attempt 1: Use a recursion that returns a boolean value to indicate whether this subtree contains all zeros
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode pruneTree(TreeNode root) {
        return isAllZeros(root) ? null : root;
    }

    private boolean isAllZeros(TreeNode root) {
        if (root.left != null && isAllZeros(root.left)) {
            root.left = null;
        }
        if (root.right != null && isAllZeros(root.right)) {
            root.right = null;
        }

        return root.left == null && root.right == null && root.val == 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.57 MB (Beats: 21.12%)

<br>
