# [LeetCode Records](../../README.md) - Question 1302 Deepest Leaves Sum

### Attempt 1: Save the maximum depth and the sum of the nodes that in the maximum depth
```java
class Solution {

    private int maxDepth;
    private int maxSum;

    public int deepestLeavesSum(TreeNode root) {
        maxDepth = 0;
        maxSum = 0;

        deepestLeavesSumRecursion(root, 0);

        return maxSum;
    }

    private void deepestLeavesSumRecursion(TreeNode root, int depth) {
        if (root == null) {
            return;
        }

        if (depth == maxDepth) {
            maxSum += root.val;
        } else if (depth > maxDepth) {
            maxDepth = depth;
            maxSum = root.val;
        }

        deepestLeavesSumRecursion(root.left, depth + 1);
        deepestLeavesSumRecursion(root.right, depth + 1);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 46.67 MB (Beats: 18.70%)

<br>
