# [LeetCode Records](../../README.md) - Question 2331 Evaluate Boolean Binary Tree

### Attempt 1: Use recursion
```java
class Solution {
    public boolean evaluateTree(TreeNode root) {
        return evaluateTreeRecursion(root) == 1;
    }

    public int evaluateTreeRecursion(TreeNode root) {
        if (root.left == null && root.right == null) {
            return root.val;
        }

        int leftVal = evaluateTreeRecursion(root.left);
        int rightVal = evaluateTreeRecursion(root.right);

        if (root.val == 2) {
            return leftVal == 1 || rightVal == 1 ? 1 : 0;
        } else {
            return leftVal == 1 && rightVal == 1 ? 1 : 0;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.32 MB (Beats: 20.34%)

<br>
