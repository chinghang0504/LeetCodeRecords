# [LeetCode Records](../../README.md) - Question 513 Find Bottom Left Tree Value

### Attempt 1: Record the maximum depth and its first reached node value
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

    private int maxDepth;
    private int maxDepthVal;

    public int findBottomLeftValue(TreeNode root) {
        maxDepth = -1;
        maxDepthVal = 0;
        
        findBottomLeftValueRecursion(root, 0);

        return maxDepthVal;
    }

    private void findBottomLeftValueRecursion(TreeNode root, int depth) {
        if (root == null) {
            return;
        } else if (depth > maxDepth) {
            maxDepth = depth;
            maxDepthVal = root.val;
        }

        findBottomLeftValueRecursion(root.left, depth + 1);
        findBottomLeftValueRecursion(root.right, depth + 1);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.60 MB (Beats: 50.23%)

<br>
