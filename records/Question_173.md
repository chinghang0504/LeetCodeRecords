# [LeetCode Records](../README.md) - Question 173 Binary Search Tree Iterator

### Attempt 1: Use an ArrayList to save the node values
```java
class BSTIterator {

    List<Integer> list = new ArrayList<>();
    int curr = 0;

    public BSTIterator(TreeNode root) {
        BSTIteratorRecursion(root);
    }

    private void BSTIteratorRecursion(TreeNode root) {
        if (root == null) {
            return;
        }

        BSTIteratorRecursion(root.left);
        list.add(root.val);
        BSTIteratorRecursion(root.right);
    }
    
    public int next() {
        return list.get(curr++);
    }
    
    public boolean hasNext() {
        return list.size() != curr;
    }
}
```
- Runtime: 16 ms (Beats: 99.72%)
- Memory: 47.89 MB (Beats: 75.75%)

<br>
