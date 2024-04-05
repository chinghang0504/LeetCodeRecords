# [LeetCode Records](../README.md) - Question 257 Binary Tree Paths

### Attempt 1: Use recursion
```java
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<>();

        binaryTreePathsRecursion(root, result, null);

        return result;
    }

    private void binaryTreePathsRecursion(TreeNode root, List<String> result, String path) {
        if (root == null) {
            return;
        }
        
        String newPath = path == null ? "" + root.val : path + "->" + root.val;
        if (root.left == null && root.right == null) {
            result.add(newPath);
            return;
        }

        binaryTreePathsRecursion(root.left, result, newPath);
        binaryTreePathsRecursion(root.right, result, newPath);
    }
}
```
- Runtime: 8 ms (Beats: 40.73%)
- Memory: 42.45 MB (Beats: 58.70%)

<br>

### Attempt 2: Use valueOf() and format()
```java
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<>();

        binaryTreePathsRecursion(root, result, null);

        return result;
    }

    private void binaryTreePathsRecursion(TreeNode root, List<String> result, String path) {
        if (root == null) {
            return;
        }
        
        String newPath = path == null ? String.valueOf(root.val) : String.format("%s->%d", path, root.val);
        if (root.left == null && root.right == null) {
            result.add(newPath);
            return;
        }

        binaryTreePathsRecursion(root.left, result, newPath);
        binaryTreePathsRecursion(root.right, result, newPath);
    }
}
```
- Runtime: 6 ms (Beats: 61.72%)
- Memory: 42.94 MB (Beats: 5.80%)

<br>

### Attempt 3: Use StringBuilder and setLength()
```java
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<>();
        StringBuilder stringBuilder = new StringBuilder();

        binaryTreePathsRecursion(root, result, stringBuilder);

        return result;
    }

    private void binaryTreePathsRecursion(TreeNode root, List<String> result, StringBuilder stringBuilder) {
        if (root == null) {
            return;
        }

        if (root.left == null && root.right == null) {
            int length = stringBuilder.length();
            stringBuilder.append(root.val);
            result.add(stringBuilder.toString());
            stringBuilder.setLength(length);
            return;
        }

        int length = stringBuilder.length();
        stringBuilder.append(root.val).append("->");
        binaryTreePathsRecursion(root.left, result, stringBuilder);
        binaryTreePathsRecursion(root.right, result, stringBuilder);
        stringBuilder.setLength(length);
    }
}
```
- Runtime: 1 ms (Beats: 99.18%)
- Memory: 42.32 MB (Beats: 70.57%)

<br>
