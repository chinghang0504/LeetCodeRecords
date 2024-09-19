# [LeetCode Records](../../README.md) - Question 1602 Find Nearest Right Node in Binary Tree

### Attempt 1: Store all the same level nodes in an ArrayList
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
    public TreeNode findNearestRightNode(TreeNode root, TreeNode u) {
        TreeNode dummy = new TreeNode();
        dummy.left = root;
        List<TreeNode> list = new ArrayList<>();
        list.add(dummy);

        int targetIndex = -1;
        while (!list.isEmpty() && targetIndex == -1) {
            List<TreeNode> nextList = new ArrayList<>();

            for (TreeNode node : list) {
                if (node.left != null) {
                    nextList.add(node.left);
                    if (node.left == u) {
                        targetIndex = nextList.size();
                    }
                }
                if (node.right != null) {
                    nextList.add(node.right);
                    if (node.right == u) {
                        targetIndex = nextList.size();
                    }
                }
            }

            list = nextList;
        }

        if (targetIndex == -1) {
            return null;
        }
        
        return targetIndex >= list.size() ? null : list.get(targetIndex);
    }
}
```
- Runtime: 12 ms (Beats: 48.48%)
- Memory: 55.00 MB (Beats: 62.12%)

<br>
