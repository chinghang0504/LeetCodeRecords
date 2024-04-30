# [LeetCode Records](../README.md) - Question 653 Two Sum IV - Input is a BST

### Attempt 1: Use a HashSet to store numbers
```java
class Solution {
    
    private Set<Integer> set;

    public boolean findTarget(TreeNode root, int k) {
        set = new HashSet<>();
        findTargetRecursion(root);

        for (int value : set) {
            int target = k - value;
            if (target != value && set.contains(target)) {
                return true;
            }
        }

        return false;
    }

    private void findTargetRecursion(TreeNode root) {
        if (root == null) {
            return;
        };

        set.add(root.val);
        findTargetRecursion(root.left);
        findTargetRecursion(root.right);
    }
}
```
- Runtime: 5 ms (Beats: 15.03%)
- Memory: 44.26 MB (Beats: 99.13%)

<br>
