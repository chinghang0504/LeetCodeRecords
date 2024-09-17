# [LeetCode Records](../../README.md) - Question 1026 Maximum Difference Between Node and Ancestor

### Attempt 1: Passing the minimum and maximum parent node values
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

    private int maxDiff;

    public int maxAncestorDiff(TreeNode root) {
        maxDiff = 0;

        maxAncestorDiff(root.left, root.val, root.val);
        maxAncestorDiff(root.right, root.val, root.val);

        return maxDiff;
    }

    private void maxAncestorDiff(TreeNode root, int minParentVal, int maxParentVal) {
        if (root == null) {
            return;
        }

        int diff1 = Math.abs(root.val - minParentVal);
        int diff2 = Math.abs(root.val - maxParentVal);
        int localMaxDiff = Math.max(diff1, diff2);
        maxDiff = Math.max(maxDiff, localMaxDiff);

        minParentVal = Math.min(minParentVal, root.val);
        maxParentVal = Math.max(maxParentVal, root.val);

        maxAncestorDiff(root.left, minParentVal, maxParentVal);
        maxAncestorDiff(root.right, minParentVal, maxParentVal);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.30 MB (Beats: 16.58%)

<br>
