# [LeetCode Records](../README.md) - Question 590 N-ary Tree Postorder Traversal

### Attempt 1: Use recursion
```java
class Solution {

    private List<Integer> result;

    public List<Integer> postorder(Node root) {
        result = new ArrayList<>();

        if (root != null) {
            postorderRecursion(root);
        }

        return result;
    }

    private void postorderRecursion(Node root) {
        for (Node child: root.children) {
            postorderRecursion(child);
        }

        result.add(root.val);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.64 MB (Beats: 43.87%)

<br>
