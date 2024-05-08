# [LeetCode Records](../../README.md) - Question 938 Range Sum of BST

### Attempt 1: Use recursion
```java
class Solution {

    private int sum;

    public int rangeSumBST(TreeNode root, int low, int high) {
        sum = 0;

        rangeSumBSTRecursion(root, low, high);

        return sum;
    }

    private void rangeSumBSTRecursion(TreeNode root, int low, int high) {
        if (root == null) {
            return;
        }

        if (low <= root.val && root.val <= high) {
            sum += root.val;
        }

        boolean isTooLow = root.val < low;
        if (!isTooLow) {
            rangeSumBSTRecursion(root.left, low, high);
        }
        boolean isTooHigh = root.val > high;
        if (!isTooHigh) {
            rangeSumBSTRecursion(root.right, low, high);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 50.96 MB (Beats: 69.23%)

<br>
