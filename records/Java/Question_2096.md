# [LeetCode Records](../../README.md) - Question 2096 Step-By-Step Directions From a Binary Tree Node to Another

### Attempt 1: Use an ArrayList to store the path from the root
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
    public String getDirections(TreeNode root, int startValue, int destValue) {
        List<Character> firstList = new ArrayList<>();
        getPath(root, startValue, firstList);

        List<Character> secondList = new ArrayList<>();
        getPath(root, destValue, secondList);

        while (!firstList.isEmpty() && !secondList.isEmpty() && firstList.getFirst() == secondList.getFirst()) {
            firstList.removeFirst();
            secondList.removeFirst();
        }

        StringBuilder stringBuilder = new StringBuilder();
        int firstListSize = firstList.size();
        for (int i = 0; i < firstListSize; i++) {
            stringBuilder.append('U');
        }
        for (char ch : secondList) {
            stringBuilder.append(ch);
        }

        return stringBuilder.toString();
    }

    private boolean getPath(TreeNode root, int startValue, List<Character> list) {
        if (root.val == startValue) {
            return true;
        }

        if (root.left != null) {
            list.addLast('L');
            if (getPath(root.left, startValue, list)) {
                return true;
            } else {
                list.removeLast();
            }
        }

        if (root.right != null) {
            list.addLast('R');
            if (getPath(root.right, startValue, list)) {
                return true;
            } else {
                list.removeLast();
            }
        }

        return false;
    }
}
```
- Runtime: 28 ms (Beats: 63.61%)
- Memory: 72.84 MB (Beats: 89.12%)

<br>
