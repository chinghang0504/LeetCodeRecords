# [LeetCode Records](../README.md) - Question 129 Sum Root to Leaf Numbers

### Attempt 1: Use recursion
```java
class Solution {

    private int total = 0;

    public int sumNumbers(TreeNode root) {
        if (root == null) {
            return 0;
        }

        sumNumbersRecursion(root, 0);

        return total;
    }

    private void sumNumbersRecursion(TreeNode root, int sum) {
        int newSum = sum * 10 + root.val;

        if (root.left == null && root.right == null) {
            total += newSum;
            return;
        }

        if (root.left != null) {
            sumNumbersRecursion(root.left, newSum);
        }
        if (root.right != null) {
            sumNumbersRecursion(root.right, newSum);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.47 MB (Beats: 17.80%)

<br>
