# [LeetCode Records](../../README.md) - Question 298 Binary Tree Longest Consecutive Sequence

### Attempt 1: Use recursion that passes the parent value and the current count
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

    private int maxCount;

    public int longestConsecutive(TreeNode root) {
        maxCount = 1;

        longestConsecutiveRecursion(root.left, root.val, 1);
        longestConsecutiveRecursion(root.right, root.val, 1);

        return maxCount;
    }

    private void longestConsecutiveRecursion(TreeNode root, int parentVal, int currCount) {
        if (root == null) {
            return;
        }

        if (root.val == parentVal + 1) {
            currCount++;
            maxCount = Math.max(maxCount, currCount);
        } else {
            currCount = 1;
        }

        longestConsecutiveRecursion(root.left, root.val, currCount);
        longestConsecutiveRecursion(root.right, root.val, currCount);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 46.08 MB (Beats: 29.55%)

<br>
