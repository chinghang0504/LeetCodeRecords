# [LeetCode Records](../../README.md) - Question 623 Add One Row to Tree

### Attempt 1: 
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 * int val;
 * TreeNode left;
 * TreeNode right;
 * TreeNode() {}
 * TreeNode(int val) { this.val = val; }
 * TreeNode(int val, TreeNode left, TreeNode right) {
 * this.val = val;
 * this.left = left;
 * this.right = right;
 * }
 * }
 */
class Solution {
    public TreeNode addOneRow(TreeNode root, int val, int depth) {
        if (depth == 1) {
            return new TreeNode(val, root, null);
        }

        addOneRowRecursion(List.of(root), val, depth, 1);
        return root;
    }

    private void addOneRowRecursion(List<TreeNode> nodes, int val, int depth, int currDepth) {
        if (currDepth + 1 != depth) {
            List<TreeNode> nextNodes = new ArrayList<>();
            for (TreeNode node : nodes) {
                if (node.left != null) {
                    nextNodes.add(node.left);
                }
                if (node.right != null) {
                    nextNodes.add(node.right);
                }
            }

            addOneRowRecursion(nextNodes, val, depth, currDepth + 1);
            return;
        }

        for (TreeNode node : nodes) {
            node.left = node.left != null ? new TreeNode(val, node.left, null) : new TreeNode(val);
            node.right = node.right != null ? new TreeNode(val, null, node.right) : new TreeNode(val);
        }
    }
}
```
- Runtime: 1 ms (Beats: 24.34%)
- Memory: 44.04 MB (Beats: 91.08%)

<br>

### Attempt 2: Use recursion to insert the nodes
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 * int val;
 * TreeNode left;
 * TreeNode right;
 * TreeNode() {}
 * TreeNode(int val) { this.val = val; }
 * TreeNode(int val, TreeNode left, TreeNode right) {
 * this.val = val;
 * this.left = left;
 * this.right = right;
 * }
 * }
 */
class Solution {
    public TreeNode addOneRow(TreeNode root, int val, int depth) {
        if (depth == 1) {
            return new TreeNode(val, root, null);
        }

        addOneRowRecursion(root, val, depth, 1);
        return root;
    }

    private void addOneRowRecursion(TreeNode root, int val, int depth, int currDepth) {
        if (root == null) {
            return;
        }

        if (currDepth + 1 != depth) {
            addOneRowRecursion(root.left, val, depth, currDepth + 1);
            addOneRowRecursion(root.right, val, depth, currDepth + 1);
        } else {
            root.left = root.left != null ? new TreeNode(val, root.left, null) : new TreeNode(val);
            root.right = root.right != null ? new TreeNode(val, null, root.right) : new TreeNode(val);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.72 MB (Beats: 11.20%)

<br>
