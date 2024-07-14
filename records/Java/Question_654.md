# [LeetCode Records](../../README.md) - Question 654 Maximum Binary Tree

### Attempt 1: Use recursion and pass the start and end indices of the array
```java
class Solution {
    public TreeNode constructMaximumBinaryTree(int[] nums) {
        TreeNode dummy = new TreeNode();

        constructMaximumBinaryTreeRecursion(nums, 0, nums.length - 1, dummy, true);

        return dummy.left;
    }

    private void constructMaximumBinaryTreeRecursion(int[] nums, int start, int end, TreeNode root, boolean isLeft) {
        if (start > end) {
            return;
        }

        int max = nums[start];
        int maxIndex = start;
        for (int i = start + 1; i <= end; i++) {
            if (nums[i] > max) {
                max = nums[i];
                maxIndex = i;
            }
        }

        TreeNode node = new TreeNode(max);
        if (isLeft) {
            root.left = node;
        } else {
            root.right = node;
        }

        constructMaximumBinaryTreeRecursion(nums, start, maxIndex - 1, node, true);
        constructMaximumBinaryTreeRecursion(nums, maxIndex + 1, end, node, false);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.73 MB (Beats: 52.02%)

<br>
