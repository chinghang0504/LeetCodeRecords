# [LeetCode Records](../../README.md) - Question 1973 Count Nodes Equal to Sum of Descendants

### Attempt 1: Use recursion to get the total sum of the subtree
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

    private int numOfNodes;

    public int equalToDescendants(TreeNode root) {
        numOfNodes = 0;

        equalToDescendantsRecursion(root);

        return numOfNodes;
    }

    private int equalToDescendantsRecursion(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int leftSum = equalToDescendantsRecursion(root.left);
        int rightSum = equalToDescendantsRecursion(root.right);
        int totalSum = leftSum + rightSum;
        
        if (totalSum == root.val) {
            numOfNodes++;
        }

        return totalSum + root.val;
    }
}
```
- Runtime: 7 ms (Beats: 100.00%)
- Memory: 75.20 MB (Beats: 92.45%)

<br>
