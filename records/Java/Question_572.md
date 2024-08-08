# [LeetCode Records](../../README.md) - Question 572 Subtree of Another Tree

### Attempt 1: Use two recursive functions
```java
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) {
            return false;
        } else if (isSubtreeRecursion(root, subRoot)) {
            return true;
        }

        if (isSubtree(root.left, subRoot)) {
            return true;
        } else if (isSubtree(root.right, subRoot)) {
            return true;
        }

        return false;
    }

    private boolean isSubtreeRecursion(TreeNode root, TreeNode subRoot) {
        if (root == null && subRoot == null) {
            return true;
        } else if (root == null || subRoot == null) {
            return false;
        } else if (root.val != subRoot.val) {
            return false;
        }

        if ((root.left == null && subRoot.left != null) || (root.left != null && subRoot.left == null)) {
            return false;
        } else if ((root.right == null && subRoot.right != null) || (root.right != null && subRoot.right == null)) {
            return false;
        }

        if (!isSubtreeRecursion(root.left, subRoot.left)) {
            return false;
        } else if (!isSubtreeRecursion(root.right, subRoot.right)) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 96.95%)
- Memory: 44.50 MB (Beats: 27.03%)

<br>
