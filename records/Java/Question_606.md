# [LeetCode Records](../../README.md) - Question 606 Construct String from Binary Tree

### Attempt 1: Return a String in the recursion
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
    public String tree2str(TreeNode root) {
        if (root == null) {
            return null;
        }

        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append(root.val);

        String leftTreeStr = tree2str(root.left);
        String rightTreeStr = tree2str(root.right);
        if (leftTreeStr != null && rightTreeStr != null) {
            stringBuilder.append("(");
            stringBuilder.append(leftTreeStr);
            stringBuilder.append(")");
            stringBuilder.append("(");
            stringBuilder.append(rightTreeStr);
            stringBuilder.append(")");
        } else if (leftTreeStr != null) {
            stringBuilder.append("(");
            stringBuilder.append(leftTreeStr);
            stringBuilder.append(")");
        } else if (rightTreeStr != null) {
            stringBuilder.append("()");
            stringBuilder.append("(");
            stringBuilder.append(rightTreeStr);
            stringBuilder.append(")");
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 4 ms (Beats: 56.92%)
- Memory: 45.74 MB (Beats: 22.24%)

<br>

### Attempt 2: Passing a StringBuilder to a recursion
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
    public String tree2str(TreeNode root) {
        StringBuilder stringBuilder = new StringBuilder();

        tree2strRecursion(root, stringBuilder);

        return stringBuilder.toString();
    }

    private void tree2strRecursion(TreeNode root, StringBuilder stringBuilder) {
        stringBuilder.append(root.val);

        if (root.left != null && root.right != null) {
            stringBuilder.append('(');
            tree2strRecursion(root.left, stringBuilder);
            stringBuilder.append(')');
            stringBuilder.append('(');
            tree2strRecursion(root.right, stringBuilder);
            stringBuilder.append(')');
        } else if (root.left != null) {
            stringBuilder.append('(');
            tree2strRecursion(root.left, stringBuilder);
            stringBuilder.append(')');
        } else if (root.right != null) {
            stringBuilder.append('(');
            stringBuilder.append(')');
            stringBuilder.append('(');
            tree2strRecursion(root.right, stringBuilder);
            stringBuilder.append(')');
        }
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.49 MB (Beats: 66.33%)

<br>
