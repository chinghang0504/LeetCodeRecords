# [LeetCode Records](../../README.md) - Question 559 Maximum Depth of N-ary Tree

### Attempt 1: Use recursion
```java
class Solution {

    private int max = 0;

    public int maxDepth(Node root) {
        if (root == null) {
            return 0;
        }

        maxDepthRecursion(root, 0);
        return max;
    }

    private void maxDepthRecursion(Node root, int currDepth) {
        if (root.children.size() == 0) {
            max = Math.max(max, currDepth + 1);
            return;
        }

        for (Node child : root.children) {
            maxDepthRecursion(child, currDepth + 1);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.78 MB (Beats: 99.00%)

<br>
