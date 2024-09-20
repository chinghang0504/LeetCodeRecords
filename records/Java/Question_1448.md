# [LeetCode Records](../../README.md) - Question 1448 Count Good Nodes in Binary Tree

### Attempt 1: Passing the maximum parent node value
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
    
    private int numOfGoodNodes;
    
    public int goodNodes(TreeNode root) {
        numOfGoodNodes = 0;

        goodNodesRecursion(root, Integer.MIN_VALUE);

        return numOfGoodNodes;
    }

    private void goodNodesRecursion(TreeNode root, int maxParentVal) {
        if (root == null) {
            return;
        }

        if (root.val >= maxParentVal) {
            maxParentVal = root.val;
            numOfGoodNodes++;
        }

        goodNodesRecursion(root.left, maxParentVal);
        goodNodesRecursion(root.right, maxParentVal);
    }
}
```
- Runtime: 2 ms (Beats: 83.98%)
- Memory: 51.96 MB (Beats: 87.01%)

<br>
