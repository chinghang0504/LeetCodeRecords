# [LeetCode Records](../../README.md) - Question 144 Binary Tree Preorder Traversal

### Attempt 1: Use recursion
```java
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        preorderTraversalRecursion(list, root);
        return list;
    }

    void preorderTraversalRecursion(List<Integer> list, TreeNode root) {
        if (root == null) {
            return;
        }

        list.add(root.val);
        preorderTraversalRecursion(list, root.left);
        preorderTraversalRecursion(list, root.right);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.84 MB (Beats: 7.92%)

<br>
