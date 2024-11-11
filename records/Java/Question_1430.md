# [LeetCode Records](../../README.md) - Question 1430 Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree

### Attempt 1: Use recusion to check from the root to the leaf
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
    public boolean isValidSequence(TreeNode root, int[] arr) {
        return isValidSequenceThroughNodes(root, arr, 0);
    }

    private boolean isValidSequenceThroughNodes(TreeNode node, int[] arr, int curr) {
        if (node == null) {
            return false;
        } else if (node.val != arr[curr]) {
            return false;
        } else if (curr == arr.length - 1) {
            return node.left == null && node.right == null;
        }

        if (isValidSequenceThroughNodes(node.left, arr, curr + 1)) {
            return true;
        } else if (isValidSequenceThroughNodes(node.right, arr, curr + 1)) {
            return true;
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.65 MB (Beats: 92.06%)

<br>
