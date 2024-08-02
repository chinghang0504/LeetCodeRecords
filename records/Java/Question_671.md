# [LeetCode Records](../../README.md) - Question 671 Second Minimum Node In a Binary Tree

### Attempt 1: Use recursion to get the second minimum value
```java
class Solution {

    int firstMin = -1;
    int secondMin = -1;

    public int findSecondMinimumValue(TreeNode root) {
        findSecondMinimumValueRecursion(root);

        return secondMin;
    }

    private void findSecondMinimumValueRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        findSecondMinimumValueRecursion(root.left);
        findSecondMinimumValueRecursion(root.right);

        if (firstMin == -1) {
            firstMin = root.val;
        } else if (root.val < firstMin) {
            secondMin = firstMin;
            firstMin = root.val;
        } else if (root.val == firstMin) {
            
        } else if (secondMin == -1) {
            secondMin = root.val;
        } else if (root.val < secondMin) {
            secondMin = root.val;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.77 MB (Beats: 56.66%)

<br>
