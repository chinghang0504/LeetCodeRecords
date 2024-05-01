# [LeetCode Records](../../README.md) - Question 700 Search in a Binary Search Tree

### Attempt 1: Use recursion
```java
class Solution {
    public TreeNode searchBST(TreeNode root, int val) {
        if (root == null) {
            return null;
        } else if (root.val == val) {
            return root;
        }

        TreeNode nextRoot = val < root.val ? root.left : root.right;
        return searchBST(nextRoot, val);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.57 MB (Beats: 97.81%)

<br>
