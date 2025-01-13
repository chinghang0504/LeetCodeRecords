# [LeetCode Records](../../README.md) - Question 437 Path Sum III

### Attempt 1: Use a HashMap to store the prefix sum and its count key-value pairs
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

    private int pathCount;
    private long targetSum;
    private Map<Long, Integer> prefixSumToCountMap;

    public int pathSum(TreeNode root, int targetSum) {
        pathCount = 0;
        this.targetSum = targetSum;
        prefixSumToCountMap = new HashMap<>();

        findNextSum(root, 0);

        return pathCount;
    }

    private void findNextSum(TreeNode root, long currSum) {
        if (root == null) {
            return;
        }

        long nextSum = currSum + root.val;
        long remaining = nextSum - targetSum;
        if (remaining == 0) {
            pathCount++;
        }
        Integer remainingCount = prefixSumToCountMap.get(remaining);
        if (remainingCount != null) {
            pathCount += remainingCount;
        }

        Integer nextSumCount = prefixSumToCountMap.get(nextSum);
        if (nextSumCount == null) {
            nextSumCount = 0;
        }
        prefixSumToCountMap.put(nextSum, nextSumCount + 1);

        findNextSum(root.left, nextSum);
        findNextSum(root.right, nextSum);

        if (nextSumCount == 0) {
            prefixSumToCountMap.remove(nextSum);
        } else {
            prefixSumToCountMap.put(nextSum, nextSumCount);
        }
    }
}
```
- Runtime: 3 ms (Beats: 96.14%)
- Memory: 44.47 MB (Beats: 31.01%)

<br>
