# [LeetCode Records](../../README.md) - Question 1315 Sum of Nodes with Even-Valued Grandparent

### Attempt 1: Pass the boolean values of the grandparent and parent
```java
class Solution {

    private int sum;

    public int sumEvenGrandparent(TreeNode root) {
        sum = 0;

        sumEvenGrandparentRecursion(root, false, false);
        
        return sum;
    }

    private void sumEvenGrandparentRecursion(TreeNode root, boolean isGrandparentEven, boolean isParentEven) {
        if (root == null) {
            return;
        }

        if (isGrandparentEven) {
            sum += root.val;
        }

        boolean isEven = root.val % 2 == 0;
        sumEvenGrandparentRecursion(root.left, isParentEven, isEven);
        sumEvenGrandparentRecursion(root.right, isParentEven, isEven);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 46.52 MB (Beats: 5.94%)

<br>
