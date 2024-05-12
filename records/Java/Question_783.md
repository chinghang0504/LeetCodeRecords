# [LeetCode Records](../../README.md) - Question 783 Minimum Distance Between BST Nodes

### Attempt 1: Use an int array to saved the values in-order
```java
class Solution {

    private int[] saved;
    private int count;

    public int minDiffInBST(TreeNode root) {
        saved = new int[100];
        count = 0;

        minDiffInBSTRecursion(root);

        int minDiff = Integer.MAX_VALUE;
        for (int i = count - 1; i > 0; i--) {
            minDiff = Math.min(minDiff, saved[i] - saved[i - 1]);
        }

        return minDiff;
    }

    private void minDiffInBSTRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        minDiffInBSTRecursion(root.left);
        saved[count] = root.val;
        count++;
        minDiffInBSTRecursion(root.right);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.78 MB (Beats: 92.15%)

<br>
