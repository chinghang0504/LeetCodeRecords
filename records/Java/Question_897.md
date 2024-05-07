# [LeetCode Records](../../README.md) - Question 897 Increasing Order Search Tree

### Attempt 1: Use recursion
```java
class Solution {

    TreeNode curr;

    public TreeNode increasingBST(TreeNode root) {
        TreeNode dummy = new TreeNode();
        curr = dummy;

        increasingBSTRecursion(root);
        curr.right = null;

        return dummy.right;
    }

    private void increasingBSTRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        increasingBSTRecursion(root.left);

        curr.right = root;
        root.left = null;
        curr = root;
        
        increasingBSTRecursion(root.right);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.89 MB (Beats: 83.89%)

<br>
