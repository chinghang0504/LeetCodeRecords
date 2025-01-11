# [LeetCode Records](../../README.md) - Question 333 Largest BST Subtree

### Attempt 1: Use recursion that returns the size, the minimum and the maximum values of the subtree
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    class Item {

        int size;
        int min;
        int max;

        Item(int size, int min, int max) {
            this.size = size;
            this.min = min;
            this.max = max;
        }
    }

    private int maxSize;

    public int largestBSTSubtree(TreeNode root) {
        if (root == null) {
            return 0;
        }

        maxSize = 0;

        getBSTSubtreeSize(root);

        return maxSize;
    }

    private Item getBSTSubtreeSize(TreeNode root) {
        int size = 0;
        int min = root.val;
        int max = root.val;
        boolean isValid = true;

        if (root.left != null) {
            Item item = getBSTSubtreeSize(root.left);
            if (item == null || item.max >= root.val) {
                isValid = false;
            } else {
                size += item.size;
                min = item.min;
            }
        }

        if (root.right != null) {
            Item item = getBSTSubtreeSize(root.right);
            if (item == null || item.min <= root.val) {
                isValid = false;
            } else {
                size += item.size;
                max = item.max;
            }
        }

        if (isValid) {
            maxSize = Math.max(maxSize, size + 1);
            return new Item(size + 1, min, max);
        } else {
            return null;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.91 MB (Beats: 89.81%)

<br>
