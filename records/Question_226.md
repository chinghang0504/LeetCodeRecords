# [LeetCode Records](../README.md) - Question 226 Invert Binary Tree

### Attempt 1: Use recursion
```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }

        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;

        invertTree(root.left);
        invertTree(root.right);

        return root;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.83 MB (Beats: 73.85%)

<br>
