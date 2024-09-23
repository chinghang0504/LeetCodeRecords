# [LeetCode Records](../../README.md) - Question 951 Flip Equivalent Binary Trees

### Attempt 1: Use recursion to check both side
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
    public boolean flipEquiv(TreeNode root1, TreeNode root2) {
        if (root1 == null && root2 == null) {
            return true;
        } else if (root1 == null || root2 == null) {
            return false;
        } else if (root1.val != root2.val) {
            return false;
        }

        if (!flipEquiv(root1.left, root2.left) && !flipEquiv(root1.left, root2.right)) {
            return false;
        }
        if (!flipEquiv(root1.right, root2.left) && !flipEquiv(root1.right, root2.right)) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.34 MB (Beats: 39.58%)

<br>
