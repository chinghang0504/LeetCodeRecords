# [LeetCode Records](../../README.md) - Question 687 Longest Univalue Path

### Attempt 1: Use recursion that returns the previous value and its edge count
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

    class Item {

        int value;
        int edgeCount;

        Item(int value) {
            this.value = value;
            this.edgeCount = 0;
        }

        Item(int value, int edgeCount) {
            this.value = value;
            this.edgeCount = edgeCount;
        }
    }

    private int maxEdgeCount;

    public int longestUnivaluePath(TreeNode root) {
        maxEdgeCount = 0;

        getSubtreeEdgeCount(root);

        return maxEdgeCount;
    }

    private Item getSubtreeEdgeCount(TreeNode root) {
        if (root == null) {
            return null;
        }

        Item leftItem = getSubtreeEdgeCount(root.left);
        Item rightItem = getSubtreeEdgeCount(root.right);
        if (leftItem != null && rightItem != null) {
            if (leftItem.value == root.val && rightItem.value == root.val) {
                maxEdgeCount = Math.max(maxEdgeCount, leftItem.edgeCount + rightItem.edgeCount + 2);
                if (leftItem.edgeCount >= rightItem.edgeCount) {
                    return new Item(root.val, leftItem.edgeCount + 1);
                } else {
                    return new Item(root.val, rightItem.edgeCount + 1);
                }
            } else if (leftItem.value == root.val) {
                int newEdgeCount = leftItem.edgeCount + 1;
                maxEdgeCount = Math.max(maxEdgeCount, newEdgeCount);
                return new Item(root.val, newEdgeCount);
            } else if (rightItem.value == root.val) {
                int newEdgeCount = rightItem.edgeCount + 1;
                maxEdgeCount = Math.max(maxEdgeCount, newEdgeCount);
                return new Item(root.val, newEdgeCount);
            } else {
                return new Item(root.val);
            }
        } else if (leftItem != null) {
            if (leftItem.value == root.val) {
                int newEdgeCount = leftItem.edgeCount + 1;
                maxEdgeCount = Math.max(maxEdgeCount, newEdgeCount);
                return new Item(root.val, newEdgeCount);
            } else {
                return new Item(root.val);
            }
        } else if (rightItem != null) {
            if (rightItem.value == root.val) {
                int newEdgeCount = rightItem.edgeCount + 1;
                maxEdgeCount = Math.max(maxEdgeCount, newEdgeCount);
                return new Item(root.val, newEdgeCount);
            } else {
                return new Item(root.val);
            }
        } else {
            return new Item(root.val);
        }
    }
}
```
- Runtime: 2 ms (Beats: 94.44%)
- Memory: 46.84 MB (Beats: 58.73%)

<br>
