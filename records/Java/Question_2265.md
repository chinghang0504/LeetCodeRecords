# [LeetCode Records](../../README.md) - Question 2265 Count Nodes Equal to Average of Subtree

### Attempt 1: Use recursion and return the total number of nodes and the total of node values
```java
class Solution {

    private int count;

    public int averageOfSubtree(TreeNode root) {
        count = 0;

        averageOfSubtreeRecursion(root);

        return count;
    }

    private int[] averageOfSubtreeRecursion(TreeNode root) {
        if (root == null) {
            return new int[]{0, 0};
        } else if (root.left == null && root.right == null) {
            count++;
            return new int[]{root.val, 1};
        }

        int[] leftTree = averageOfSubtreeRecursion(root.left);
        int[] rightTree = averageOfSubtreeRecursion(root.right);
        int totalValue = leftTree[0] + rightTree[0] + root.val;
        int totalNum = leftTree[1] + rightTree[1] + 1;
        if (totalValue / totalNum == root.val) {
            count++;
        }

        return new int[]{totalValue, totalNum};
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.03 MB (Beats: 48.03%)

<br>
