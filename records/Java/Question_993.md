# [LeetCode Records](../../README.md) - Question 993 Cousins in Binary Tree

### Attempt 1: Use the recursion to find the depth and parent of x and y
```java
class Solution {

    private int xParent, xDepth;
    private int yParent, yDepth;

    public boolean isCousins(TreeNode root, int x, int y) {
        isCousinsRecursion(root, x, y, 0, 0);

        return xDepth == yDepth && xParent != yParent;
    }

    private void isCousinsRecursion(TreeNode root, int x, int y, int parent, int depth) {
        if (root == null) {
            return;
        }

        if (root.val == x) {
            xParent = parent;
            xDepth = depth + 1;
        } else if (root.val == y) {
            yParent = parent;
            yDepth = depth + 1;
        }

        isCousinsRecursion(root.left, x, y, root.val, depth + 1);
        isCousinsRecursion(root.right, x, y, root.val, depth + 1);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.64 MB (Beats: 98.57%)

<br>
