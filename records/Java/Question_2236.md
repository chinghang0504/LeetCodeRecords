# [LeetCode Records](../../README.md) - Question 2236 Root Equals Sum of Children

### Attempt 1: 
```java
class Solution {
    public boolean checkTree(TreeNode root) {
        return root.left.val + root.right.val == root.val;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.32 MB (Beats: 19.51%)

<br>
