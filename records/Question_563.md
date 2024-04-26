# [LeetCode Records](../README.md) - Question 563 Binary Tree Tilt

### Attempt 1: Use recursion
```java
class Solution {

    private int sum = 0;

    public int findTilt(TreeNode root) {
        findTiltRecursion(root);
        return sum;
    }

    private int findTiltRecursion(TreeNode root) {
        if (root == null) {
            return 0;
        } else if (root.left == null && root.right == null) {
            return root.val;
        }

        int leftVal = findTiltRecursion(root.left);
        int rightVal = findTiltRecursion(root.right);
        sum += Math.abs(leftVal - rightVal);
        return leftVal + rightVal + root.val;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.19 MB (Beats: 53.25%)

<br>
