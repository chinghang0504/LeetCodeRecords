# [LeetCode Records](../../README.md) - Question 124 Binary Tree Maximum Path Sum

### Attempt 1: Calculate the local max sum and the return max sum
```java
class Solution {

    private int maxSum = Integer.MIN_VALUE;

    public int maxPathSum(TreeNode root) {
        maxPathSumRecursion(root);

        return maxSum;
    }

    private int maxPathSumRecursion(TreeNode root) {
        // Empty node
        if (root == null) {
            return 0;
        }

        // One node
        if (root.left == null && root.right == null) {
            maxSum = Math.max(maxSum, root.val);
            return root.val;
        }

        // Calculate each sum
        int returnMaxSum = root.val;
        int left = maxPathSumRecursion(root.left);
        int right = maxPathSumRecursion(root.right);

        // Calculate the return max sum
        returnMaxSum = Math.max(returnMaxSum, root.val + left);
        returnMaxSum = Math.max(returnMaxSum, root.val + right);

        // Calculate the local max sum
        int localMaxSum = Math.max(returnMaxSum, root.val + left + right);
        maxSum = Math.max(maxSum, localMaxSum);

        return returnMaxSum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.93 MB (Beats: 83.37%)

<br>
