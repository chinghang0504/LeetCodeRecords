# [LeetCode Records](../README.md) - Question 589 N-ary Tree Preorder Traversal

### Attempt 1: Use  recursion
```java
class Solution {

    private List<Integer> result;

    public List<Integer> preorder(Node root) {
        result = new ArrayList<>();

        if (root != null) {
            preorderRecursion(root);
        }

        return result;
    }

    private void preorderRecursion(Node root) {
        result.add(root.val);

        for (Node child: root.children) {
            preorderRecursion(child);
        }   
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.50 MB (Beats: 74.23%)

<br>
