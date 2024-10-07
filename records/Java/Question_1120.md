# [LeetCode Records](../../README.md) - Question 1120 Maximum Average Subtree

### Attempt 1: Use a recursion to return an int[] that stores the sum of values and the number of nodes
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

    private double maxAverage;

    public double maximumAverageSubtree(TreeNode root) {
        maxAverage = 0.0;

        maximumAverageSubtreeRecursion(root);

        return maxAverage;
    }

    private int[] maximumAverageSubtreeRecursion(TreeNode root) {
        if (root == null) {
            return new int[]{ 0, 0 };
        }

        int[] left = maximumAverageSubtreeRecursion(root.left);
        int[] right = maximumAverageSubtreeRecursion(root.right);
        
        int totalVals = left[0] + right[0] + root.val;
        int numOfNodes = left[1] + right[1] + 1;
        maxAverage = Math.max(maxAverage, (double)totalVals / numOfNodes);

        return new int[]{ totalVals, numOfNodes };
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.80 MB (Beats: 89.81%)

<br>
