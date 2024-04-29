# [LeetCode Records](../README.md) - Question 617 Merge Two Binary Trees

### Attempt 1: Use recursion
```java
class Solution {
    public TreeNode mergeTrees(TreeNode root1, TreeNode root2) {
        if (root1 == null && root2 == null) {
            return null;
        }

        TreeNode node = null;
        if (root1 == null) {
            node = new TreeNode(root2.val);
            node.left = mergeTrees(null, root2.left);
            node.right = mergeTrees(null, root2.right);
        } else if (root2 == null) {
            node = new TreeNode(root1.val);
            node.left = mergeTrees(root1.left, null);
            node.right = mergeTrees(root1.right, null);
        } else {
            node = new TreeNode(root1.val + root2.val);
            node.left = mergeTrees(root1.left, root2.left);
            node.right = mergeTrees(root1.right, root2.right);
        }

        return node;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.92 MB (Beats: 33.09%)

<br>
