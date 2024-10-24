# [LeetCode Records](../../README.md) - Question 250 Count Univalue Subtrees

### Attempt 1: Use recursion to return a boolean value that indicates all subtrees have the same value
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

    private int count;

    public int countUnivalSubtrees(TreeNode root) {
        if (root == null) {
            return 0;
        }

        count = 0;
        countUnivalSubtreesRecursion(root);

        return count;
    }

    private boolean countUnivalSubtreesRecursion(TreeNode root) {
        if (root.left != null && root.right != null) {
            boolean left = countUnivalSubtreesRecursion(root.left);
            boolean right = countUnivalSubtreesRecursion(root.right);
            if (left && right && root.left.val == root.val && root.right.val == root.val) {
                count++;
                return true;
            } else {
                return false;
            }
        } else if (root.left != null) {
            boolean left = countUnivalSubtreesRecursion(root.left);
            if (left && root.left.val == root.val) {
                count++;
                return true;
            } else {
                return false;
            }
        } else if (root.right != null) {
            boolean right = countUnivalSubtreesRecursion(root.right);
            if (right && root.right.val == root.val) {
                count++;
                return true;
            } else {
                return false;
            }
        } else {
            count++;
            return true;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.15 MB (Beats: 98.65%)

<br>
