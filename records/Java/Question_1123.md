# [LeetCode Records](../../README.md) - Question 1123 Lowest Common Ancestor of Deepest Leaves

### Attempt 1: Use recursion that returns a pair of the TreeNode and the depth
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
    public TreeNode lcaDeepestLeaves(TreeNode root) {
        return lcaDeepestLeavesRecursion(root, 0).getKey();
    }

    public Pair<TreeNode, Integer> lcaDeepestLeavesRecursion(TreeNode root, int depth) {
        if (root == null) {
            return null;
        }

        Pair<TreeNode, Integer> left = lcaDeepestLeavesRecursion(root.left, depth + 1);
        Pair<TreeNode, Integer> right = lcaDeepestLeavesRecursion(root.right, depth + 1);
        if (left != null && right != null) {
            int depth1 = left.getValue();
            int depth2 = right.getValue();
            if (depth1 == depth2) {
                return new Pair<>(root, depth1);
            } else if (depth1 > depth2) {
                return left;
            } else {
                return right;
            }
        } else if (left != null) {
            return left;
        } else if (right != null) {
            return right;
        } else {
            return new Pair<>(root, depth);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.60 MB (Beats: 98.59%)

<br>
