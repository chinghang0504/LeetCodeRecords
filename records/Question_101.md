# [LeetCode Records](../README.md) - Question 101 Symmetric Tree

### Attempt 1: Check left.left and right.right at the same time
```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if (root == null) {
            return true;
        }

        return isSymmetricRecursion(root.left, root.right);
    }

    boolean isSymmetricRecursion(TreeNode left, TreeNode right) {
        if (left == null && right == null) {
            return true;
        } else if (left == null || right == null) {
            return false;
        }

        if (left.val != right.val) {
            return false;
        }

        if (!isSymmetricRecursion(left.left, right.right)) {
            return false;
        }
        if (!isSymmetricRecursion(left.right, right.left)) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.02 MB (Beats: 12.59%)

<br>
