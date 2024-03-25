# [LeetCode Records](../README.md) - Question 104 Maximum Depth of Binary Tree

### Attempt 1: Compare the left depth and the right depth
```java
class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int leftDepth = 1 + maxDepth(root.left);
        int rightDepth = 1 + maxDepth(root.right);

        return Math.max(leftDepth, rightDepth);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.73 MB (Beats: 25.15%)

<br>
