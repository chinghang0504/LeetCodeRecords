# [LeetCode Records](../../README.md) - Question 1038 Binary Search Tree to Greater Sum Tree

### Attempt 1: Use recursion and a field to save the current sum
```java
class Solution {

    private int currSum;

    public TreeNode bstToGst(TreeNode root) {
        TreeNode copyRoot = new TreeNode();

        currSum = 0;
        bstToGstRecursion(root, copyRoot);

        return copyRoot;
    }

    private void bstToGstRecursion(TreeNode root, TreeNode copyRoot) {
        if (root.right != null) {
            TreeNode copyNode = new TreeNode();
            copyRoot.right = copyNode;
            bstToGstRecursion(root.right, copyNode);
        }

        currSum += root.val;
        copyRoot.val = currSum;

        if (root.left != null) {
            TreeNode copyNode = new TreeNode();
            copyRoot.left = copyNode;
            bstToGstRecursion(root.left, copyNode);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.35 MB (Beats: 9.79%)

<br>

### Attempt 2: Use recursion and pass the current sum as an argument
```java
class Solution {

    public TreeNode bstToGst(TreeNode root) {
        TreeNode copyRoot = new TreeNode();

        bstToGstRecursion(root, copyRoot, 0);

        return copyRoot;
    }

    private int bstToGstRecursion(TreeNode root, TreeNode copyRoot, int currSum) {
        if (root.right != null) {
            TreeNode copyNode = new TreeNode();
            copyRoot.right = copyNode;
            currSum = bstToGstRecursion(root.right, copyNode, currSum);
        }

        currSum += root.val;
        copyRoot.val = currSum;

        if (root.left != null) {
            TreeNode copyNode = new TreeNode();
            copyRoot.left = copyNode;
            currSum = bstToGstRecursion(root.left, copyNode, currSum);
        }

        return currSum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.88 MB (Beats: 63.01%)

<br>
