# [LeetCode Records](../../README.md) - Question 1644 Lowest Common Ancestor of a Binary Tree II

### Attempt 1: Search the tree twice times. For the first time, find both target nodes exist. For the second time, find the common node.
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

    private boolean isPExist;
    private boolean isQExist;

    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        isPExist = false;
        isQExist = false;

        findPAndQ(root, p, q);
        if (!isPExist || !isQExist) {
            return null;
        }

        return getLowestCommonAncestor(root, p, q);
    }

    private boolean findPAndQ(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null) {
            return false;
        } else if (root == p) {
            isPExist = true;
            if (isQExist) {
                return true;
            }
        } else if (root == q) {
            isQExist = true;
            if (isPExist) {
                return true;
            }
        }

        if (findPAndQ(root.left, p, q)) {
            return true;
        }
        if (findPAndQ(root.right, p, q)) {
            return true;
        }

        return false;
    }

    private TreeNode getLowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null) {
            return null;
        } else if (root == p || root == q) {
            return root;
        }

        TreeNode left = getLowestCommonAncestor(root.left, p, q);
        TreeNode right = getLowestCommonAncestor(root.right, p, q);
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
- Runtime: 7 ms (Beats: 99.97%)
- Memory: 47.27 MB (Beats: 30.66%)

<br>
