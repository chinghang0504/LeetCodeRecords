# [LeetCode Records](../../README.md) - Question 669 Trim a Binary Search Tree

### Attempt 1: Use recursion that returns a boolean value that indicates the node is invalid
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 * int val;
 * TreeNode left;
 * TreeNode right;
 * TreeNode() {}
 * TreeNode(int val) { this.val = val; }
 * TreeNode(int val, TreeNode left, TreeNode right) {
 * this.val = val;
 * this.left = left;
 * this.right = right;
 * }
 * }
 */
class Solution {
    public TreeNode trimBST(TreeNode root, int low, int high) {
        TreeNode dummy = new TreeNode();
        dummy.left = root;

        trimBSTRecursion(dummy, low, high);

        return dummy.left;
    }

    private boolean trimBSTRecursion(TreeNode root, int low, int high) {
        if (root == null) {
            return false;
        }
        
        if (trimBSTRecursion(root.left, low, high)) {
            if (root.left.left != null) {
                root.left = root.left.left;
            } else if (root.left.right != null) {
                root.left = root.left.right;
            } else {
                root.left = null;
            }
        }

        if (trimBSTRecursion(root.right, low, high)) {
            if (root.right.left != null) {
                root.right = root.right.left;
            } else if (root.right.right != null) {
                root.right = root.right.right;
            } else {
                root.right = null;
            }
        }

        return root.val < low || root.val > high;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.62 MB (Beats: 17.86%)

<br>
