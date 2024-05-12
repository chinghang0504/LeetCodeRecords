# [LeetCode Records](../../README.md) - Question 530 Minimum Absolute Difference in BST

### Attempt 1: Use an int[] to saved the values in-order
```java
class Solution {

    private int[] saved;
    private int count;

    public int getMinimumDifference(TreeNode root) {
        saved = new int[10000];
        count = 0;

        getMinimumDifferenceRecursion(root);

        int minDiff = Integer.MAX_VALUE;
        for (int i = count - 1; i > 0; i--) {
            minDiff = Math.min(minDiff, saved[i] - saved[i - 1]);
        }

        return minDiff;
    }

    private void getMinimumDifferenceRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        getMinimumDifferenceRecursion(root.left);
        saved[count] = root.val;
        count++;
        getMinimumDifferenceRecursion(root.right);
    }
}
```
- Runtime: 2 ms (Beats: 19.96%)
- Memory: 44.56 MB (Beats: 28.86%)

<br>

### Attempt 2: Use a final static int[] to saved the values in-order
```java
class Solution {

    private final static int[] saved = new int[10000];
    private int count;

    public int getMinimumDifference(TreeNode root) {
        count = 0;

        getMinimumDifferenceRecursion(root);

        int minDiff = Integer.MAX_VALUE;
        for (int i = count - 1; i > 0; i--) {
            minDiff = Math.min(minDiff, saved[i] - saved[i - 1]);
        }

        return minDiff;
    }

    private void getMinimumDifferenceRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        getMinimumDifferenceRecursion(root.left);
        saved[count] = root.val;
        count++;
        getMinimumDifferenceRecursion(root.right);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.91 MB (Beats: 7.87%)

<br>
