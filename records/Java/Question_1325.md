# [LeetCode Records](../../README.md) - Question 1325 Delete Leaves With a Given Value

### Attempt 1: Use recursion to check and remove the target
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
    public TreeNode removeLeafNodes(TreeNode root, int target) {
        TreeNode dummy = new TreeNode();
        dummy.left = root;
        
        removeLeafNodesRecursive(dummy, target);

        return dummy.left;
    }

    private void removeLeafNodesRecursive(TreeNode root, int target) {
        if (root.left != null) {
            removeLeafNodesRecursive(root.left, target);
        }
        if (root.right != null) {
            removeLeafNodesRecursive(root.right, target);
        }

        if (root.left != null && isLeafAndTarget(root.left, target)) {
            root.left = null;
        }
        if (root.right != null && isLeafAndTarget(root.right, target)) {
            root.right = null;
        }
    }

    private boolean isLeafAndTarget(TreeNode root, int target) {
        return root.left == null && root.right == null && root.val == target;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.44 MB (Beats: 18.98%)

<br>
