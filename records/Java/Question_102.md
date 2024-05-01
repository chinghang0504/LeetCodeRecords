# [LeetCode Records](../../README.md) - Question 102 Binary Tree Level Order Traversal

### Attempt 1: Use two ArrayList to record the current level of nodes and integers
```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return result;
        }

        List<TreeNode> prevNodes = new ArrayList<>();
        prevNodes.add(root);

        while (!prevNodes.isEmpty()) {
            List<TreeNode> nodes = new ArrayList<>();
            List<Integer> integers = new ArrayList<>();
            
            for (TreeNode node: prevNodes) {
                integers.add(node.val);
                if (node.left != null) {
                    nodes.add(node.left);
                }
                if (node.right != null) {
                    nodes.add(node.right);
                }
            }

            result.add(integers);
            prevNodes = nodes;
        }        

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 88.22%)
- Memory: 44.79 MB (Beats: 66.87%)

<br>
