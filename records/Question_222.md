# [LeetCode Records](../README.md) - Question 222 Count Complete Tree Nodes

### Attempt 1: Use recursion
```java
class Solution {
    public int countNodes(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int count = 0;
        if (root.left != null) {
            count += countNodes(root.left);
        }
        if (root.right != null) {
            count += countNodes(root.right);
        }

        return count + 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 47.49 MB (Beats: 62.65%)

<br>
