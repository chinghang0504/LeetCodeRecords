# [LeetCode Records](../../README.md) - Question 1609 Even Odd Tree

### Attempt 1: Use an ArrayList to store the child nodes
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
    public boolean isEvenOddTree(TreeNode root) {
        List<TreeNode> list = new ArrayList<>();
        list.add(root);

        boolean isOddLevel = true;
        while (!list.isEmpty()) {
            List<TreeNode> nextList = new ArrayList<>();

            if (isOddLevel) {
                int prevVal = Integer.MIN_VALUE;
                for (TreeNode node : list) {
                    if (node.val % 2 == 0 || node.val <= prevVal) {
                        return false;
                    } else {
                        prevVal = node.val;
                    }

                    if (node.left != null) {
                        nextList.add(node.left);
                    }
                    if (node.right != null) {
                        nextList.add(node.right);
                    }
                }
            } else {
                int prevVal = Integer.MAX_VALUE;
                for (TreeNode node : list) {
                    if (node.val % 2 == 1 || node.val >= prevVal) {
                        return false;
                    } else {
                        prevVal = node.val;
                    }

                    if (node.left != null) {
                        nextList.add(node.left);
                    }
                    if (node.right != null) {
                        nextList.add(node.right);
                    }
                }
            }

            list = nextList;
            isOddLevel = !isOddLevel;
        }

        return true;
    }
}
```
- Runtime: 12 ms (Beats: 37.65%)
- Memory: 68.18 MB (Beats: 13.01%)

<br>
