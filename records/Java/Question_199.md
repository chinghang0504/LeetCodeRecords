# [LeetCode Records](../../README.md) - Question 199 Binary Tree Right Side View

### Attempt 1: Use ArrayList to record the current level of nodes
```java
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        
        List<TreeNode> prevNodes = new ArrayList<>();
        prevNodes.add(root);

        while (!prevNodes.isEmpty()) {
            int size = prevNodes.size();
            result.add(prevNodes.get(0).val);

            List<TreeNode> nodes = new ArrayList<>();
            for (int i = 0; i < size; i++) {
                TreeNode curr = prevNodes.get(i);
                if (curr.right != null) {
                    nodes.add(curr.right);
                }
                if (curr.left != null) {
                    nodes.add(curr.left);
                }
            }
            prevNodes = nodes;
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 68.51%)
- Memory: 42.48 MB (Beats: 8.31%)

<br>
