# [LeetCode Records](../../README.md) - Question 145 Binary Tree Postorder Traversal

### Attempt 1: Use recursion
```java
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        postorderTraversalRecursion(list, root);
        return list;
    }

    void postorderTraversalRecursion(List<Integer> list, TreeNode root) {
        if (root == null) {
            return;
        }

        postorderTraversalRecursion(list, root.left);
        postorderTraversalRecursion(list, root.right);
        list.add(root.val);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.77 MB (Beats: 14.55%)

<br>
