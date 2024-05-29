# [LeetCode Records](../../README.md) - Question 1469 Find All The Lonely Nodes

### Attempt 1: Pass the status of parent node
```java
class Solution {
    public List<Integer> getLonelyNodes(TreeNode root) {
        List<Integer> result = new ArrayList<>();

        getLonelyNodesRecursion(root, false, result);

        return result;
    }

    private void getLonelyNodesRecursion(TreeNode root, boolean isOnly, List<Integer> result) {
        if (root == null) {
            return;
        }

        if (isOnly) {
            result.add(root.val);
        }
        isOnly = root.left != null && root.right == null || root.left == null && root.right != null;

        getLonelyNodesRecursion(root.left, isOnly, result);
        getLonelyNodesRecursion(root.right, isOnly, result);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.61 MB (Beats: 36.20%)

<br>
