# [LeetCode Records](../../README.md) - Question 1457 Pseudo-Palindromic Paths in a Binary Tree

### Attempt 1: Use an int[] to store the number counts
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 * int val;
 * TreeNode left;
 * TreeNode right;
 * TreeNode() {}
 * TreeNode(int val) { this.val = val; }
 * TreeNode(int val, TreeNode left, TreeNode right) {
 * this.val = val;
 * this.left = left;
 * this.right = right;
 * }
 * }
 */
class Solution {

    private int count;
    private int[] counts;

    public int pseudoPalindromicPaths(TreeNode root) {
        count = 0;
        counts = new int[10];

        pseudoPalindromicPathsRecursion(root);

        return count;
    }

    private void pseudoPalindromicPathsRecursion(TreeNode root) {
        counts[root.val]++;

        if (root.left == null && root.right == null) {
            checkPalindromicPath();
            counts[root.val]--;
            return;
        }

        if (root.left != null) {
            pseudoPalindromicPathsRecursion(root.left);
        }
        if (root.right != null) {
            pseudoPalindromicPathsRecursion(root.right);
        }

        counts[root.val]--;
    }

    private void checkPalindromicPath() {
        int oddCount = 0;
        for (int i = 1; i <= 9; i++) {
            if (counts[i] % 2 == 1) {
                oddCount++;

                if (oddCount == 2) {
                    return;
                }
            }
        }

        count++;
    }
}
```
- Runtime: 10 ms (Beats: 75.67%)
- Memory: 69.10 MB (Beats: 91.39%)

<br>
