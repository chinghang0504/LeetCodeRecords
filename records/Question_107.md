# [LeetCode Records](../README.md) - Question 107 Binary Tree Level Order Traversal II

### Attempt 1: Use two ArrayList to record the current level of nodes and integers
```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
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

        return result.reversed();
    }
}
```
- Runtime: 1 ms (Beats: 86.49%)
- Memory: 42.90 MB (Beats: 44.30%)

<br>
