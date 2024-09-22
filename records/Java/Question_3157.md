# [LeetCode Records](../../README.md) - Question 3157 Find the Level of Tree with Minimum Sum

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

    public int minimumLevel(TreeNode root) {
        Long minSum = Long.MAX_VALUE;
        int minSumLevel = 0;
        int currLevel = 1;
        List<TreeNode> nodes = new ArrayList<>();
        nodes.add(root);
        
        while (!nodes.isEmpty()) {
            List<TreeNode> nextNodes = new ArrayList<>();

            Long localSum = 0L;
            for (TreeNode node : nodes) {
                localSum += node.val;

                if (node.left != null) {
                    nextNodes.add(node.left);
                }
                if (node.right != null) {
                    nextNodes.add(node.right);
                }
            }

            if (localSum < minSum) {
                minSum = localSum;
                minSumLevel = currLevel;
            }

            nodes = nextNodes;
            currLevel++;
        }

        return minSumLevel;
    }
}
```
- Runtime: 12 ms (Beats: 35.20%)
- Memory: 70.19 MB (Beats: 23.20%)

<br>
