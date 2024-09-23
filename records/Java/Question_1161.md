# [LeetCode Records](../../README.md) - Question 1161 Maximum Level Sum of a Binary Tree

### Attempt 1: Use an ArrayList to store the same level nodes
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
    public int maxLevelSum(TreeNode root) {
        List<TreeNode> list = new ArrayList<>();
        list.add(root);

        int maxSum = Integer.MIN_VALUE;
        int maxSumLevel = 0;
        int level = 1;
        while (!list.isEmpty()) {
            List<TreeNode> nextList = new ArrayList<>();

            int sum = 0;
            for (TreeNode node : list) {
                sum += node.val;
                if (node.left != null) {
                    nextList.add(node.left);
                }
                if (node.right != null) {
                    nextList.add(node.right);
                }
            }
            if (sum > maxSum) {
                maxSum = sum;
                maxSumLevel = level;
            }

            list = nextList;
            level++;
        }

        return maxSumLevel;
    }
}
```
- Runtime: 9 ms (Beats: 41.53%)
- Memory: 46.32 MB (Beats: 91.78%)

<br>
