# [LeetCode Records](../../README.md) - Question 3319 K-th Largest Perfect Subtree Size in Binary Tree

### Attempt 1: Use an ArrayList to store the perfect subtree count
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

    private List<Integer> list;

    public int kthLargestPerfectSubtree(TreeNode root, int k) {
        list = new ArrayList<>();

        perfectSubtreeCount(root);

        list.sort(null);
        int size = list.size();

        return k > size ? -1 : list.get(size - k);    
    }

    private int perfectSubtreeCount(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int left = perfectSubtreeCount(root.left);
        int right = perfectSubtreeCount(root.right);
        if (left == -1 || right == -1 || left != right) {
            return -1;
        }

        int count = left + right + 1;
        list.add(count);
        return count;
    }
}
```
- Runtime: 11 ms (Beats: 64.86%)
- Memory: 45.31 MB (Beats: 43.24%)

<br>
