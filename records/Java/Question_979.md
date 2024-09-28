# [LeetCode Records](../../README.md) - Question 979 Distribute Coins in Binary Tree

### Attempt 1: Use a recursion to return the number of coins that own
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

    private int numOfMoves;

    public int distributeCoins(TreeNode root) {
        numOfMoves = 0;

        distributeCoinsRecursion(root);

        return numOfMoves;
    }

    private int distributeCoinsRecursion(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int count = root.val - 1;
        count += distributeCoinsRecursion(root.left);
        count += distributeCoinsRecursion(root.right);

        if (count != 0) {
            numOfMoves += Math.abs(count);
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.57 MB (Beats: 97.26%)

<br>
