# [LeetCode Records](../../README.md) - Question 1660 Correct a Binary Tree

### Attempt 1: Store the same level nodes in the ArrayList
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode correctBinaryTree(TreeNode root) {
        List<TreeNode> list = new ArrayList<>();
        list.add(root);

        while (!list.isEmpty()) {
            List<TreeNode> nextList = new ArrayList<>();

            for (TreeNode node : list) {
                if (node.right != null) {
                    nextList.add(node.right);
                    if (nextList.contains(node.right.right)) {
                        node.right = null;
                        return root;
                    }
                }
                if (node.left != null) {
                    nextList.add(node.left);
                    if (nextList.contains(node.left.right)) {
                        node.left = null;
                        return root;
                    }
                }
            }

            list = nextList;
        }

        return root;
    }
}
```
- Runtime: 7 ms (Beats: 55.21%)
- Memory: 46.77 MB (Beats: 63.19%)

<br>
