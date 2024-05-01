# [LeetCode Records](../../README.md) - Question 108 Converted Sorted Array to Binary Search Tree

### Attempt 1: Insert the middle and split left and right trees
```java
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        int middle = nums.length / 2;
        TreeNode root = new TreeNode(nums[middle]);

        addLeaf(nums, root, 0, middle - 1, true);
        addLeaf(nums, root, middle + 1, nums.length - 1, false);

        return root;
    }

    void addLeaf(int[] nums, TreeNode root, int start, int end, boolean leftTree) {
        if (start > end) {
            return;
        } else if (start == end) {
            TreeNode node = new TreeNode(nums[start]);
            if (leftTree) {
                root.left = node;
            } else {
                root.right = node;
            }
            return;
        }

        int middle = (start + end) / 2;
        TreeNode node = new TreeNode(nums[middle]);
        if (leftTree) {
            root.left = node;
        } else {
            root.right = node;
        }

        addLeaf(nums, node, start, middle - 1, true);
        addLeaf(nums, node, middle + 1, end, false);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.23 MB (Beats: 34.70%)

<br>
