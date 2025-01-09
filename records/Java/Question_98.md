# [LeetCode Records](../../README.md) - Question 98 Validate Binary Search Tree

### Attempt 1: Use two TreeSet to track the left minimum value and the right maximum value
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
    public boolean isValidBST(TreeNode root) {
        SortedSet<Integer> lSet = new TreeSet<>();
        SortedSet<Integer> rSet = new TreeSet<>();

        return isValidBSTRecursion(lSet, rSet, root);
    }

    private boolean isValidBSTRecursion(SortedSet<Integer> lSet, SortedSet<Integer> rSet, TreeNode root) {
        if (!lSet.isEmpty() && root.val >= lSet.first()) {
            return false;
        } else if (!rSet.isEmpty() && root.val <= rSet.last()) {
            return false;
        }

        if (root.left != null) {
            lSet.add(root.val);
            if (!isValidBSTRecursion(lSet, rSet, root.left)) {
                return false;
            }
            lSet.remove(root.val);
        }
        if (root.right != null) {
            rSet.add(root.val);
            if (!isValidBSTRecursion(lSet, rSet, root.right)) {
                return false;
            }
            rSet.remove(root.val);
        }

        return true;
    }
}
```
- Runtime: 3 ms (Beats: 4.60%)
- Memory: 44.56 MB (Beats: 17.73%)

<br>

### Attempt 2: Use two variables to track the left minimum value and the right maximum value
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
    public boolean isValidBST(TreeNode root) {
        return isValidBSTRecursion(root, null, null);
    }

    private boolean isValidBSTRecursion(TreeNode root, Integer leftMin, Integer rightMax) {
        if (leftMin != null && root.val >= leftMin) {
            return false;
        } else if (rightMax != null && root.val <= rightMax) {
            return false;
        }

        if (root.left != null && !isValidBSTRecursion(root.left, leftMin == null ? root.val : Math.min(leftMin, root.val), rightMax)) {
            return false;
        } else if (root.right != null && !isValidBSTRecursion(root.right, leftMin, rightMax == null ? root.val : Math.max(rightMax, root.val))) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.89 MB (Beats: 40.78%)

<br>
