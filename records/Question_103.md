# [LeetCode Records](../README.md) - Question 103 Binary Tree Zigzag Level Order Traversal

### Attempt 1: Use two ArrayList to record the current level of nodes and integers
```java
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return result;
        }

        boolean isLeft = true;
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

            if (isLeft) {
                result.add(integers);
            } else {
                result.add(integers.reversed());
            }
            isLeft = !isLeft;
            prevNodes = nodes;
        }        

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 75.11%)
- Memory: 42.20 MB (Beats: 21.34%)

<br>
