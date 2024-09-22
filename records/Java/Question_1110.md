# [LeetCode Records](../../README.md) - Question 1110 Delete Nodes And Return Forest

### Attempt 1: Convert the int[] of deleted nodes to a HashSet
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

    private List<TreeNode> nodes;
    private Set<Integer> deletedNodes;

    public List<TreeNode> delNodes(TreeNode root, int[] to_delete) {
        nodes = new ArrayList<>();

        deletedNodes = new HashSet<>();
        for (int num : to_delete) {
            deletedNodes.add(num);
        }

        delNodesRecursion(root, true);
        
        return nodes;
    }

    private boolean delNodesRecursion(TreeNode root, boolean isParent) {
        if (root == null) {
            return false;
        } else if (deletedNodes.contains(root.val)) {
            delNodesRecursion(root.left, true);
            delNodesRecursion(root.right, true);
            return true;
        }

        if (isParent) {
            nodes.add(root);
        }
        if (delNodesRecursion(root.left, false)) {
            root.left = null;
        }
        if (delNodesRecursion(root.right, false)) {
            root.right = null;
        }
        return false;
    }
}
```
- Runtime: 1 ms (Beats: 93.14%)
- Memory: 44.65 MB (Beats: 71.36%)

<br>
