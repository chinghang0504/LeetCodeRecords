# [LeetCode Records](../README.md) - Question 543 Diameter of Binary Tree

### Attempt 1: Use recursion
```java
class Solution {

    private int max = 0;

    public int diameterOfBinaryTree(TreeNode root) {
        diameterOfBinaryTreeRecursion(root);
        return max;
    }

    private int diameterOfBinaryTreeRecursion(TreeNode root) {
        if (root == null) {
            return 0;
        } else if (root.left == null && root.right == null) {
            return 1;
        }

        int leftLength = diameterOfBinaryTreeRecursion(root.left);
        int rightLength = diameterOfBinaryTreeRecursion(root.right);

        max = Math.max(max, leftLength + rightLength);
        return 1 + (leftLength >= rightLength ? leftLength : rightLength);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.69 MB (Beats: 22.61%)

<br>
