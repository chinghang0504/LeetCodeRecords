# [LeetCode Records](../../README.md) - Question 114 Flatten Binary Tree to Linked List

### Attempt 1: Save the left and right nodes before recursion
```java
class Solution {
    private TreeNode current;
    
    public void flatten(TreeNode root) {
        if (root == null) {
            return;
        }

        TreeNode rootLeft = root.left;
        TreeNode rootRight = root.right;

        current = root;
        current.left = null;
        current.right = null;
        
        flattenRecursion(rootLeft);
        flattenRecursion(rootRight);
    }
    
    private void flattenRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        TreeNode rootLeft = root.left;
        TreeNode rootRight = root.right;
        
        current.right = root;
        current = root;
        current.left = null;
        current.right = null;
        
        flattenRecursion(rootLeft);
        flattenRecursion(rootRight);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.11 MB (Beats: 36.24%)

<br>
