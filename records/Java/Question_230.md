# [LeetCode Records](../../README.md) - Question 230 Kth Smallest Element in a BST

### Attempt 1: Use recursion to follow the order
```java
class Solution {

    private int count = 0;

    public int kthSmallest(TreeNode root, int k) {
        return kthSmallestRecursion(root, k);
    }

    private int kthSmallestRecursion(TreeNode root, int k) {
        if (root.left == null && root.right == null) {
            count++;
            return root.val;
        }

        if (root.left != null) {
            int left = kthSmallestRecursion(root.left, k);
            if (count == k) {
                return left;
            }
        }

        count++;
        if (count == k) {
            return root.val;
        }

        if (root.right != null) {
            int right = kthSmallestRecursion(root.right, k);
            if (count == k) {
                return right;
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.31 MB (Beats: 43.17%)

<br>
