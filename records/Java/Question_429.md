# [LeetCode Records](../../README.md) - Question 429 N-ary Tree Level Order Traversal

### Attempt 1: Loop for each level of nodes
```java
class Solution {
    public List<List<Integer>> levelOrder(Node root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return result;
        }

        List<Node> list = new ArrayList<>();
        list.add(root);

        while (!list.isEmpty()) {
            List<Integer> intList = new ArrayList<>();
            List<Node> nextList = new ArrayList<>();
            
            for (Node node : list) {
                intList.add(node.val);
                for (Node childNode : node.children) {
                    nextList.add(childNode);
                }
            }

            result.add(intList);
            list = nextList;
        }

        return result;
    }
}
```
- Runtime: 3 ms (Beats: 77.28%)
- Memory: 44.57 MB (Beats: 71.71%)

<br>
