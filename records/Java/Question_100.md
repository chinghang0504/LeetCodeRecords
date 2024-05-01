# [LeetCode Records](../../README.md) - Question 100 Same Tree

### Attempt 1: Check root, val, left, and right
```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        } else if (p == null || q == null) {
            return false;
        }

        if (p.val != q.val) {
            return false;
        }

        if (!isSameTree(p.left, q.left)) {
            return false;
        } else if (!isSameTree(p.right, q.right)) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.54 MB (Beats: 8.83%)

<br>
