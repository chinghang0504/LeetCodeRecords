# [LeetCode Records](../../README.md) - Question 2689 Extract Kth Character From The Rope Tree

### Attempt 1: Use recursion to get the left and right strings
```java
class Solution {
    public char getKthCharacter(RopeTreeNode root, int k) {
        String result = getKthCharacterRecursion(root);

        return result.charAt(k - 1);
    }

    private String getKthCharacterRecursion(RopeTreeNode root) {
        if (root == null) {
            return null;
        } else if (root.len == 0) {
            return root.val;
        }

        String leftString = getKthCharacterRecursion(root.left);
        leftString = leftString != null ? leftString : "";
        String rightString = getKthCharacterRecursion(root.right);
        rightString = rightString != null ? rightString : "";
        
        return leftString + rightString;
    }
}
```
- Runtime: 1 ms (Beats: 73.61%)
- Memory: 52.02 MB (Beats: 56.94%)

<br>
