# [LeetCode Records](../README.md) - Question 404 Sum of Left Leaves

### Attempt 1: Use recursion
```java
class Solution {
    
    int sum = 0;
    
    public int sumOfLeftLeaves(TreeNode root) {
        sumOfLeftLeavesRecursion(root, false);
        return sum;
    }
    
    private void sumOfLeftLeavesRecursion(TreeNode root, boolean isLeft) {
        if (root == null) {
            return;
        } else if (isLeft && root.left == null && root.right == null) {
            sum += root.val;
            return;
        }

        sumOfLeftLeavesRecursion(root.left, true);
        sumOfLeftLeavesRecursion(root.right, false);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.72 MB (Beats: 7.96%)

<br>
