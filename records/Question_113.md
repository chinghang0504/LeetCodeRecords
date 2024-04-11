# [LeetCode Records](../README.md) - Question 113 Path Sum II

### Attempt 1: Use a ArrayList to record the current list
```java
class Solution {

    private List<List<Integer>> result;
    private List<Integer> list;

    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        result = new ArrayList<>();
        if (root == null) {
            return result;
        }

        list = new ArrayList<>();

        pathSumRecursion(root, targetSum, 0);

        return result;
    }

    private void pathSumRecursion(TreeNode root, int targetSum, int sum) {
        int newSum = root.val + sum;
        list.add(root.val);

        if (root.left == null && root.right == null) {
            if (newSum == targetSum) {
                result.add(new ArrayList<>(list));
            }
            list.removeLast();
            return;
        }

        if (root.left != null) {
            pathSumRecursion(root.left, targetSum, newSum);
        }
        if (root.right != null) {
            pathSumRecursion(root.right, targetSum, newSum);
        }

        list.removeLast();
    }
}
```
- Runtime: 1 ms (Beats: 99.91%)
- Memory: 44.30 MB (Beats: 79.54%)

<br>
