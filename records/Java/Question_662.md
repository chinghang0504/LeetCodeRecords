# [LeetCode Records](../../README.md) - Question 662 Maximum Width of Binary Tree

### Attempt 1: Use a HashMap to store the minimum index and the maximum index of each depth
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

    private Map<Integer, int[]> depthToMinMaxMap;

    public int widthOfBinaryTree(TreeNode root) {
        depthToMinMaxMap = new HashMap<>();
        addMinMax(root, 0, 0);

        int maxWidth = 0;
        for (int[] minMax : depthToMinMaxMap.values()) {
            maxWidth = Math.max(maxWidth, minMax[1] - minMax[0]);
        };

        return maxWidth + 1;
    }

    private void addMinMax(TreeNode root, int depth, int currIndex) {
        if (root == null) {
            return;
        }

        int[] minMax = depthToMinMaxMap.get(depth);
        if (minMax == null) {
            minMax = new int[]{ currIndex, currIndex };
            depthToMinMaxMap.put(depth, minMax);
        } else {
            minMax[1] = currIndex;
        }

        addMinMax(root.left, depth + 1, currIndex + currIndex);
        addMinMax(root.right, depth + 1, currIndex + currIndex + 1);
    }
}
```
- Runtime: 2 ms (Beats: 38.24%)
- Memory: 43.80 MB (Beats: 23.42%)

<br>

### Attempt 2: Use a HashMap to store the minimum index of each depth
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

    private Map<Integer, Integer> depthToMinIndexMap;
    private int maxWidth;

    public int widthOfBinaryTree(TreeNode root) {
        depthToMinIndexMap = new HashMap<>();
        maxWidth = 0;

        addMinIndex(root, 0, 0);

        return maxWidth + 1;
    }

    private void addMinIndex(TreeNode root, int depth, int currIndex) {
        if (root == null) {
            return;
        }

        Integer minIndex = depthToMinIndexMap.get(depth);
        if (minIndex == null) {
            depthToMinIndexMap.put(depth, currIndex);
        } else {
            maxWidth = Math.max(maxWidth, currIndex - minIndex);
        }

        addMinIndex(root.left, depth + 1, currIndex + currIndex);
        addMinIndex(root.right, depth + 1, currIndex + currIndex + 1);
    }
}
```
- Runtime: 1 ms (Beats: 98.50%)
- Memory: 43.84 MB (Beats: 23.42%)

<br>

### Attempt 3: Use an int[] to store the minimum index of each depth
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

    private int[] minIndices;
    private int maxWidth;

    public int widthOfBinaryTree(TreeNode root) {
        minIndices = new int[3000];
        maxWidth = 0;

        addMinIndex(root, 0, 0);

        return maxWidth + 1;
    }

    private void addMinIndex(TreeNode root, int depth, int currIndex) {
        if (root == null) {
            return;
        }

        if (minIndices[depth] == 0) {
            minIndices[depth] = currIndex + 1;
        } else {
            maxWidth = Math.max(maxWidth, currIndex + 1 - minIndices[depth]);
        }

        addMinIndex(root.left, depth + 1, currIndex + currIndex);
        addMinIndex(root.right, depth + 1, currIndex + currIndex + 1);
    }
}
```
- Runtime: 1 ms (Beats: 98.50%)
- Memory: 44.40 MB (Beats: 7.13%)

<br>
