# [LeetCode Records](../../README.md) - Question 1740 Find Distance in a Binary Tree

### Attempt 1: Use an ArrayList to store the path of the target node
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
    public int findDistance(TreeNode root, int p, int q) {
        List<Character> firstList = new ArrayList<>();
        List<Character> secondList = new ArrayList<>();

        getPath(root, p, firstList);
        getPath(root, q, secondList);

        int size1 = firstList.size();
        int size2 = secondList.size();
        int minSize = Math.min(size1, size2);
        int i = 0;
        for (; i < minSize; i++) {
            if (firstList.get(i) != secondList.get(i)) {
                break;
            }
        }
        
        return size1 + size2 - i - i;
    }

    private boolean getPath(TreeNode root, int target, List<Character> list) {
        if (root.val == target) {
            return true;
        }

        if (root.left != null) {
            list.addLast('L');
            if (getPath(root.left, target, list)) {
                return true;
            } else {
                list.removeLast();
            }
        }

        if (root.right != null) {
            list.addLast('R');
            if (getPath(root.right, target, list)) {
                return true;
            } else {
                list.removeLast();
            }
        }

        return false;
    }
}
```
- Runtime: 2 ms (Beats: 23.19%)
- Memory: 45.79 MB (Beats: 62.91%)

<br>
