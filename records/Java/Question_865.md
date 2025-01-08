# [LeetCode Records](../../README.md) - Question 865 Smallest Subtree with all the Deepest Nodes

### Attempt 1: Use recursion to get the parent of all the deepest node and its maximum depth
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

        TreeNode node;
        int depth;

        Item(TreeNode node, int depth) {
            this.node = node;
            this.depth = depth;
        }
    }

    public TreeNode subtreeWithAllDeepest(TreeNode root) {
        return subtreeWithAllDeepestRecursion(root, 0).node;
    }

    private Item subtreeWithAllDeepestRecursion(TreeNode root, int depth) {
        if (root.left != null && root.right != null) {
            Item leftItem = subtreeWithAllDeepestRecursion(root.left, depth + 1);
            Item rightItem = subtreeWithAllDeepestRecursion(root.right, depth + 1);
            if (leftItem.depth > rightItem.depth) {
                return leftItem;
            } else if (leftItem.depth < rightItem.depth) {
                return rightItem;
            } else {
                return new Item(root, leftItem.depth);
            }
        } else if (root.left != null) {
            return subtreeWithAllDeepestRecursion(root.left, depth + 1);
        } else if (root.right != null) {
            return subtreeWithAllDeepestRecursion(root.right, depth + 1);
        } else {
            return new Item(root, depth);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.57 MB (Beats: 81.91%)

<br>
