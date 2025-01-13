# [LeetCode Records](../../README.md) - Question 536 Construct Binary Tree from String

### Attempt 1: Use recursion to return the TreeNode of the current level
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
    public TreeNode str2tree(String s) {
        char[] arr = s.toCharArray();
        if (arr.length == 0) {
            return null;
        }

        boolean isNegative = false;
        int i = 0;
        if (arr[i] == '-') {
            isNegative = true;
            i++;
        }

        int rootVal = 0;
        while (i < arr.length && arr[i] != '(') {
            rootVal = rootVal * 10 + arr[i] - '0';
            i++;
        }
        if (isNegative) {
            rootVal *= -1;
        }
        if (i == arr.length) {
            return new TreeNode(rootVal);
        }
        i++;

        int leftStart = i;
        int openedNum = 1;
        while (openedNum > 0) {
            i++;
            if (arr[i] == '(') {
                openedNum++;
            } else if (arr[i] == ')') {
                openedNum--;
            }
        }
        int leftEnd = i;
        int rightStart = i + 2;
        int rightEnd = arr.length - 1;

        TreeNode root = new TreeNode(rootVal);
        root.left = str2tree(s.substring(leftStart, leftEnd));
        if (i + 2 < arr.length) {
            root.right = str2tree(s.substring(rightStart, rightEnd));
        }

        return root;
    }
}
```
- Runtime: 5 ms (Beats: 66.87%)
- Memory: 45.11 MB (Beats: 49.21%)

<br>
