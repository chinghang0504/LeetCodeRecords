# [LeetCode Records](../../README.md) - Question 106 Construct Binary Tree from Inorder and Postorder Traversal

### Attempt 1: Find the root in inorder and postorder arrays
```java
class Solution {
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        return buildTreeRecursion(inorder, postorder, 0, inorder.length - 1, 0, inorder.length - 1);
    }

    private TreeNode buildTreeRecursion(int[] inorder, int[] postorder, int inorder_start, int inorder_end, int postorder_start, int postorder_end) {
        if (postorder_start > postorder_end) {
            return null;
        } else if (postorder_start == postorder_end) {
            return new TreeNode(postorder[postorder_start]);
        }

        int rootVal = postorder[postorder_end];
        TreeNode root = new TreeNode(rootVal);
        int rootIndexInorder = 0;
        for (int i = inorder_start; i <= inorder_end; i++) {
            if (inorder[i] == rootVal) {
                rootIndexInorder = i;
            }
        }
        int leftTreeSize = rootIndexInorder - inorder_start;

        root.left = buildTreeRecursion(inorder, postorder, inorder_start, rootIndexInorder - 1, postorder_start, postorder_start + leftTreeSize - 1);
        root.right = buildTreeRecursion(inorder, postorder, rootIndexInorder + 1, inorder_end, postorder_start + leftTreeSize, postorder_end - 1);

        return root;
    }
}
```
- Runtime: 3 ms (Beats: 33.29%)
- Memory: 44.36 MB (Beats: 37.21%)

<br>
