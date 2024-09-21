# [LeetCode Records](../../README.md) - Question 2196 Create Binary Tree From Descriptions

### Attempt 1: Use a HashMap to store the TreeNodes
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
    public TreeNode createBinaryTree(int[][] descriptions) {
        Map<Integer, TreeNode> map = new HashMap<>();
        Set<Integer> parentVals = new HashSet<>();
        Set<Integer> childVals = new HashSet<>();

        for (int[] description : descriptions) {
            int parentVal = description[0];
            int childVal = description[1];

            parentVals.add(parentVal);
            childVals.add(childVal);

            TreeNode parentNode = map.get(parentVal);
            if (parentNode == null) {
                parentNode = new TreeNode(parentVal);
                map.put(parentVal, parentNode);
            }

            TreeNode childNode = map.get(childVal);
            if (childNode == null) {
                childNode = new TreeNode(childVal);
                map.put(childVal, childNode);
            }

            if (description[2] == 1) {
                parentNode.left = childNode;
            } else {
                parentNode.right = childNode;
            }
        }

        for (int parentVal : parentVals) {
            if (!childVals.contains(parentVal)) {
                return map.get(parentVal);
            }
        }

        return null;
    }
}
```
- Runtime: 72 ms (Beats: 39.17%)
- Memory: 55.90 MB (Beats: 55.80%)

<br>
