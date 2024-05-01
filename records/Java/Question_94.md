# [LeetCode Records](../../README.md) - Question 94 Binary Tree Inorder Traversal

### Attempt 1: Traversal: left -> root -> right
```java
class Solution {
    List<Integer> list = new ArrayList<Integer>();

    public List<Integer> inorderTraversal(TreeNode root) {
        inorderTraversalRecursion(root);
        return list;
    }

    void inorderTraversalRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        if (root.left != null) {
            inorderTraversalRecursion(root.left);
        }

        list.add(root.val);
        
        if (root.right != null) {
            inorderTraversalRecursion(root.right);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.20 MB (Beats: 86.79%)

<br>
