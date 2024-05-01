# [LeetCode Records](../../README.md) - Question 105 Construct Binary Tree from Preorder and Inorder Traversal

### Attempt 1: Find the root in preorder and inorder arrays
```java
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        return buildTreeRecursion(preorder, inorder, 0, preorder.length - 1, 0, preorder.length - 1);
    }

    private TreeNode buildTreeRecursion(int[] preorder, int[] inorder, int preorder_start, int preorder_end, int inorder_start, int inorder_end) {
        if (preorder_start > preorder_end) {
            return null;
        } else if (preorder_start == preorder_end) {
            return new TreeNode(preorder[preorder_start]);
        }

        int rootVal = preorder[preorder_start];
        TreeNode root = new TreeNode(rootVal);
        int rootIndexInorder = 0;
        for (int i = inorder_start; i <= inorder_end; i++) {
            if (inorder[i] == rootVal) {
                rootIndexInorder = i;
            }
        }
        int leftTreeSize = rootIndexInorder - inorder_start;

        root.left = buildTreeRecursion(preorder, inorder, preorder_start + 1, preorder_start + leftTreeSize, inorder_start, inorder_start + leftTreeSize - 1);
        root.right = buildTreeRecursion(preorder, inorder, preorder_start + leftTreeSize + 1, preorder_end, rootIndexInorder + 1, inorder_end);

        return root;
    }
}
```
- Runtime: 3 ms (Beats: 44.14%)
- Memory: 44.42 MB (Beats: 32.16%)

<br>
