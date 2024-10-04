# [LeetCode Records](../../README.md) - Question 538 Convert BST to Greater Tree

### Attempt 1: Use recursion traversing from the right to the root and from the root to the left
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
    public TreeNode convertBST(TreeNode root) {
        convertBSTRecursion(root, 0);

        return root;
    }

    private int convertBSTRecursion(TreeNode root, int currSum) {
        if (root == null) {
            return currSum;
        }

        int right = convertBSTRecursion(root.right, currSum);
        root.val += right;
        int left = convertBSTRecursion(root.left, root.val);
        return left;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.23 MB (Beats: 51.99%)

<br>
