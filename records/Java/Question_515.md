# [LeetCode Records](../../README.md) - Question 515 Find Largest Value in Each Tree Row

### Attempt 1: Use recursion to pass the current depth of the node
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

    private List<Integer> ans;

    public List<Integer> largestValues(TreeNode root) {
        ans = new ArrayList<>();

        largestValuesRecursion(root, 0);

        return ans;
    }

    private void largestValuesRecursion(TreeNode root, int depth) {
        if (root == null) {
            return;
        } else if (depth >= ans.size()) {
            ans.add(root.val);
        } else {
            ans.set(depth, Math.max(ans.get(depth), root.val));
        }

        largestValuesRecursion(root.left, depth + 1);
        largestValuesRecursion(root.right, depth + 1);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.36 MB (Beats: 53.35%)

<br>
