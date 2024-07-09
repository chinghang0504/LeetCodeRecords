# [LeetCode Records](../../README.md) - Question 965 Univalued Binary Tree

### Attempt 1: Use recursion
```java
class Solution {
    public boolean isUnivalTree(TreeNode root) {
        if (root == null) {
            return true;
        }

        return isUnivalTreeRecursion(root, root.val);
    }

    private boolean isUnivalTreeRecursion(TreeNode root, int val) {
        if (root == null) {
            return true;
        } else if (root.val != val) {
            return false;
        }

        if (!isUnivalTreeRecursion(root.left, val)) {
            return false;
        }
        if (!isUnivalTreeRecursion(root.right, val)) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.90 MB (Beats: 72.89%)

<br>
