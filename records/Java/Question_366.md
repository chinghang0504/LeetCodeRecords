# [LeetCode Records](../../README.md) - Question 366 Find Leaves of Binary Tree

### Attempt 1: Use the recursion to reach the leaves and remove the leaves
```java
class Solution {
    public List<List<Integer>> findLeaves(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();

        while (root.left != null || root.right != null) {
            List<Integer> currList = new ArrayList<>();
            findLeavesRecursion(root, currList);
            result.add(currList);
        }
        result.add(List.of(root.val));

        return result;
    }

    private boolean findLeavesRecursion(TreeNode root, List<Integer> currList) {
        if (root == null) {
            return false;
        } else if (root.left == null && root.right == null) {
            currList.add(root.val);
            return true;
        }

        if (findLeavesRecursion(root.left, currList)) {
            root.left = null;
        }
        if (findLeavesRecursion(root.right, currList)) {
            root.right = null;
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.84 MB (Beats: 26.88%)

<br>
