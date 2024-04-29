# [LeetCode Records](../README.md) - Question 637 Average of Levels in Binary Tree

### Attempt 1: Use an ArrayList to save the nodes of the same level
```java
class Solution {
    public List<Double> averageOfLevels(TreeNode root) {
        List<Double> result = new ArrayList<>();
        List<TreeNode> prevNodes = new ArrayList<>();
        prevNodes.add(root);

        while (!prevNodes.isEmpty()) {
            double sum = 0;
            int count = 0;

            List<TreeNode> nodes = new ArrayList<>();
            Iterator<TreeNode> iterator = prevNodes.iterator();
            while (iterator.hasNext()) {
                TreeNode node = iterator.next();
                sum += node.val;
                count++;

                if (node.left != null) {
                    nodes.add(node.left);
                }
                if (node.right != null) {
                    nodes.add(node.right);
                }
            }

            result.add(sum / count);
            prevNodes = nodes;
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 96.00%)
- Memory: 45.27 MB (Beats: 89.72%)

<br>
