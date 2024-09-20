# [LeetCode Records](../../README.md) - Question 1612 Check If Two Expression Trees are Equivalent

### Attempt 1: Count the number of characters in the tree
```java
/**
 * Definition for a binary tree node.
 * class Node {
 *     char val;
 *     Node left;
 *     Node right;
 *     Node() {this.val = ' ';}
 *     Node(char val) { this.val = val; }
 *     Node(char val, Node left, Node right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean checkEquivalence(Node root1, Node root2) {
        int[] counts1 = new int[26];
        int[] counts2 = new int[26];

        getCountsRecursion(root1, counts1);
        getCountsRecursion(root2, counts2);

        return Arrays.equals(counts1, counts2);
    }

    private void getCountsRecursion(Node root, int[] counts) {
        if (root == null) {
            return;
        } else if (root.left == null && root.right == null) {
            counts[root.val - 'a']++;
            return;
        }

        getCountsRecursion(root.left, counts);
        getCountsRecursion(root.right, counts);
    }
}
```
- Runtime: 4 ms (Beats: 100.00%)
- Memory: 45.83 MB (Beats: 44.19%)

<br>
