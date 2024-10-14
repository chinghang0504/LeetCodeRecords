# [LeetCode Records](../../README.md) - Question 1372 Longest ZigZag Path in a Binary Tree

### Attempt 1: Use recursion to pass the boolean value that indicates from left or right and the current length
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 * int val;
 * TreeNode left;
 * TreeNode right;
 * TreeNode() {}
 * TreeNode(int val) { this.val = val; }
 * TreeNode(int val, TreeNode left, TreeNode right) {
 * this.val = val;
 * this.left = left;
 * this.right = right;
 * }
 * }
 */
class Solution {

    private int maxLength;

    public int longestZigZag(TreeNode root) {
        maxLength = 0;

        longestZigZagRecursion(root.left, true, 1);
        longestZigZagRecursion(root.right, false, 1);

        return maxLength;
    }

    private void longestZigZagRecursion(TreeNode root, boolean isLeft, int currLength) {
        if (root == null) {
            return;
        }
        
        maxLength = Math.max(maxLength, currLength);

        if (isLeft) {
            longestZigZagRecursion(root.left, true, 1);
            longestZigZagRecursion(root.right, false, currLength + 1);
        } else {
            longestZigZagRecursion(root.left, true, currLength + 1);
            longestZigZagRecursion(root.right, false, 1);
        }
    }
}
```
- Runtime: 4 ms (Beats: 96.07%)
- Memory: 55.05 MB (Beats: 42.25%)

<br>
