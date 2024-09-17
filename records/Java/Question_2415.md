# [LeetCode Records](../../README.md) - Question 2415 Reverse Odd Levels of Binary Tree

### Attempt 1: Use an ArrayList to store the same level nodes
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
    public TreeNode reverseOddLevels(TreeNode root) {
        int depth = 0;
        List<TreeNode> nodes = new ArrayList<>();
        nodes.add(root);

        while (!nodes.isEmpty()) {
            if (depth % 2 == 1) {
                int size = nodes.size();
                for (int i = 0; i < size / 2; i++) {
                    TreeNode left = nodes.get(i);
                    TreeNode right = nodes.get(size - i - 1);
                    int temp = left.val;
                    left.val = right.val;
                    right.val = temp;
                }
            }

            List<TreeNode> nextNodes = new ArrayList<>();
            if (nodes.get(0).left != null) {
                for (TreeNode node : nodes) {
                    nextNodes.add(node.left);
                    nextNodes.add(node.right);
                }
            }

            nodes = nextNodes;
            depth++;
        }

        return root;
    }
}
```
- Runtime: 7 ms (Beats: 44.99%)
- Memory: 47.73 MB (Beats: 94.35%)

<br>
