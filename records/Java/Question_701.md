# [LeetCode Records](../../README.md) - Question 701 Insert into a Binary Search Tree

### Attempt 1: Use recursion to insert a new node into the BST
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
    public TreeNode insertIntoBST(TreeNode root, int val) {
        if (root == null) {
            return new TreeNode(val);
        }

        insertIntoBSTRecursion(root, val);
        return root;
    }

    private void insertIntoBSTRecursion(TreeNode root, int val) {
        if (val < root.val) {
            if (root.left == null) {
                root.left = new TreeNode(val);
            } else {
                insertIntoBSTRecursion(root.left, val);
            }
        } else {
            if (root.right == null) {
                root.right = new TreeNode(val);
            } else {
                insertIntoBSTRecursion(root.right, val);
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.20 MB (Beats: 39.27%)

<br>
