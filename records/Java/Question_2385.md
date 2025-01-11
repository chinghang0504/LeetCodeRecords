# [LeetCode Records](../../README.md) - Question 2385 Amount of Time for Binary Tree to Be Infected

### Attempt 1: Use an ArrayList to store the path of the start and compare the path with each node
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

    private int maxLen;
    private List<Integer> startList;
    private int startListSize;

    public int amountOfTime(TreeNode root, int start) {
        startList = new ArrayList<>();
        createStartList(start, root);
        startListSize = startList.size();
        
        maxLen = 0;

        compareToStartList(root, 0, 0);
        
        return maxLen;
    }

    private boolean createStartList(int start, TreeNode root) {
        startList.addLast(root.val);
        
        if (root.val == start) {
            return true;
        }

        if (root.left != null) {
            if (createStartList(start, root.left)) {
                return true;
            }
        }
        if (root.right != null) {
            if (createStartList(start, root.right)) {
                return true;
            }
        }

        startList.removeLast();
        return false;
    }

    private void compareToStartList(TreeNode root, int currI, int numOfSameChars) {
        if (numOfSameChars == currI && startListSize > currI && startList.get(currI) == root.val) {
            numOfSameChars++;
            maxLen = Math.max(maxLen, startListSize - numOfSameChars);
        } else {
            maxLen = Math.max(maxLen, startListSize - numOfSameChars + currI + 1 - numOfSameChars);
        }
        
        if (root.left != null) {
            compareToStartList(root.left, currI + 1, numOfSameChars);
        }
        if (root.right != null) {
            compareToStartList(root.right, currI + 1, numOfSameChars);
        }
    }
}
```
- Runtime: 15 ms (Beats: 84.06%)
- Memory: 81.17 MB (Beats: 51.87%)

<br>
