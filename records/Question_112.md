# [LeetCode Records](../README.md) - Question 112 Path Sum

### Attempt 1: Use recursion
```java
class Solution {
    public boolean hasPathSum(TreeNode root, int targetSum) {
        if (root == null) {
            return false;
        }

        return hasPathSumRecursion(root, targetSum, 0);
    }

    boolean hasPathSumRecursion(TreeNode root, int targetSum, int currSum) {
        if (root.left == null && root.right == null) {
            return targetSum == currSum + root.val;
        }

        if (root.left != null && hasPathSumRecursion(root.left, targetSum, currSum + root.val)) {
                return true;
        }
        if (root.right != null && hasPathSumRecursion(root.right, targetSum, currSum + root.val)) {
                return true;
        }
        
        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.46 MB (Beats: 11.42%)

<br>
