# [LeetCode Records](../README.md) - Question 110 Balanced Binary Tree

### Attempt 1: Compare the left and right height and throw an exception if it is not balanced
```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        try {
            getHeight(root);
        } catch (Exception e) {
            return false;
        }

        return true;
    }

    int getHeight(TreeNode root) throws Exception {
        if (root == null) {
            return 0;
        }

        int leftHeight = getHeight(root.left);
        int rightHeight = getHeight(root.right);

        if (Math.abs(leftHeight - rightHeight) >= 2) {
            throw new Exception();
        }

        return 1 + Math.max(leftHeight, rightHeight);
    }
}
```
- Runtime: 1 ms (Beats: 32.83%)
- Memory: 43.80 MB (Beats: 97.65%)

<br>

### Attempt 2: Compare the left and right height and check the balance of the subtrees
```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        if (root == null) {
            return true;
        }

        int leftHeight = getHeight(root.left);
        int rightHeight = getHeight(root.right);

        return Math.abs(leftHeight - rightHeight) < 2 && isBalanced(root.left) && isBalanced(root.right);
    }

    int getHeight(TreeNode root) {
        if (root == null) {
            return 0;
        }

        return 1 + Math.max(getHeight(root.left), getHeight(root.right));
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.02 MB (Beats: 82.28%)

<br>

### Attempt 3: Compare the left and right height and check the balance at the same time without using exception
```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        int height = getHeight(root);

        return height != -1;
    }

    int getHeight(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int leftHeight = getHeight(root.left);
        if (leftHeight == -1) {
            return -1;
        }

        int rightHeight = getHeight(root.right);
        if (rightHeight == -1) {
            return -1;
        }

        if (Math.abs(leftHeight - rightHeight) >= 2) {
            return -1;
        }

        return 1 + Math.max(leftHeight, rightHeight);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.96 MB (Beats: 90.61%)

<br>
