# [LeetCode Records](../../README.md) - Question 1022 Sum of Root To Leaf Binary Numbers

### Attempt 1: Use the recursion
```java
class Solution {

    private int sum;

    public int sumRootToLeaf(TreeNode root) {
        sum = 0;

        sumRootToLeafRecursion(root, 0);

        return sum;
    }

    private void sumRootToLeafRecursion(TreeNode root, int val) {
        if (root == null) {
            return;
        }

        val <<= 1;
        val += root.val;
        if (root.left == null && root.right == null) {
            sum += val;
            return;
        }

        sumRootToLeafRecursion(root.left, val);
        sumRootToLeafRecursion(root.right, val);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.85 MB (Beats: 55.83%)

<br>
