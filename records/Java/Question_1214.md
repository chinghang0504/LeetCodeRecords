# [LeetCode Records](../../README.md) - Question 1214 Two Sum BSTs

### Attempt 1: Use HashSet to store the node values
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
    public boolean twoSumBSTs(TreeNode root1, TreeNode root2, int target) {
        Set<Integer> set1 = new HashSet<>();
        Set<Integer> set2 = new HashSet<>();

        storeNodes(set1, root1);
        storeNodes(set2, root2);

        for (int num : set1) {
            if (set2.contains(target - num)) {
                return true;
            }
        }

        return false;
    }

    private void storeNodes(Set<Integer> set, TreeNode root) {
        if (root == null) {
            return;
        }

        set.add(root.val);
        storeNodes(set, root.left);
        storeNodes(set, root.right);
    }
}
```
- Runtime: 6 ms (Beats: 34.32%)
- Memory: 45.00 MB (Beats: 85.59%)

<br>
