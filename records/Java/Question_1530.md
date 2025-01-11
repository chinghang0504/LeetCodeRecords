# [LeetCode Records](../../README.md) - Question 1530 Number of Good Leaf Nodes Pairs

### Attempt 1: Use an ArrayList to store all the leaf paths
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

    private List<String> leafPathList;

    public int countPairs(TreeNode root, int distance) {
        leafPathList = new ArrayList<>();
        addLeafPaths(new StringBuilder(), root);

        int count = 0;
        int listSize = leafPathList.size();
        for (int i = 0; i < listSize - 1; i++) {
            for (int j = i + 1; j < listSize; j++) {
                if (isGood(distance, leafPathList.get(i), leafPathList.get(j))) {
                    count++;
                }
            }
        }

        return count;
    }

    private void addLeafPaths(StringBuilder stringBuilder, TreeNode root) {
        if (root.left == null && root.right == null) {
            leafPathList.add(stringBuilder.toString());
            return;
        }

        if (root.left != null) {
            stringBuilder.append('L');
            addLeafPaths(stringBuilder, root.left);
            stringBuilder.deleteCharAt(stringBuilder.length() - 1);
        }
        if (root.right != null) {
            stringBuilder.append('R');
            addLeafPaths(stringBuilder, root.right);
            stringBuilder.deleteCharAt(stringBuilder.length() - 1);
        }
    }

    private boolean isGood(int distance, String path1, String path2) {
        int pathLen1 = path1.length();
        int pathLen2 = path2.length();
        int i = 0;
        int end = Math.min(pathLen1, pathLen2);
        while (i < end && path1.charAt(i) == path2.charAt(i)) {
            i++;
        }

        if (i == 0) {
            return pathLen1 + pathLen2 <= distance;
        } else {
            return pathLen1 - i + pathLen2 - i <= distance;
        }
    }
}
```
- Runtime: 59 ms (Beats: 19.56%)
- Memory: 44.91 MB (Beats: 58.08%)

<br>
