# [LeetCode Records](../../README.md) - Question 1379 Find a Corresponding Node of a Binary Tree in a Clone of That Tree

### Attempt 1: Use recursion
```java
class Solution {
    public final TreeNode getTargetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
        if (original == null) {
            return null;
        } else if (original == target) {
            return cloned;
        }

        TreeNode leftNode = getTargetCopy(original.left, cloned.left, target);
        if (leftNode != null) {
            return leftNode;
        }

        TreeNode rightNode = getTargetCopy(original.right, cloned.right, target);
        if (rightNode != null) {
            return rightNode;
        }

        return null;
    }
}
```
- Runtime: 1 ms (Beats: 97.29%)
- Memory: 49.66 MB (Beats: 29.27%)

<br>
