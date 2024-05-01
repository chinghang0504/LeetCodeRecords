# [LeetCode Records](../../README.md) - Question 270 Closest Binary Search Tree Value

### Attempt 1: Use recursion to test each node
```java
class Solution {

    private int closestVal = 0;
    private double closestDiff = Integer.MAX_VALUE;

    public int closestValue(TreeNode root, double target) {
        closestValueRecursion(root, target);
        return closestVal;
    }

    private void closestValueRecursion(TreeNode root, double target) {
        if (root == null) {
            return;
        }

        double diff = Math.abs(target - root.val);
        if (diff < closestDiff) {
            closestDiff = diff;
            closestVal = root.val;
        } else if (diff == closestDiff) {
            closestVal = Math.min(closestVal, root.val);
        }

        closestValueRecursion(root.left, target);
        closestValueRecursion(root.right, target);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.03 MB (Beats: 40.17%)

<br>
