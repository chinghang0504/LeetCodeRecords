# [LeetCode Records](../../README.md) - Question 1522 Diameter of N-Ary Tree

### Attempt 1: Sum the longest and the second longest distances of childrens
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> children;

    
    public Node() {
        children = new ArrayList<Node>();
    }
    
    public Node(int _val) {
        val = _val;
        children = new ArrayList<Node>();
    }
    
    public Node(int _val,ArrayList<Node> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {

    private int maxLength;

    public int diameter(Node root) {
        maxLength = 0;

        diameterRecursion(root);

        return maxLength;
    }

    private int diameterRecursion(Node root) {
        int max1 = 0;
        int max2 = 0;

        for (Node node : root.children) {
            int length = diameterRecursion(node);
            if (length > max1) {
                max2 = max1;
                max1 = length;
            } else if (length == max1) {
                max2 = length;
            } else if (length > max2) {
                max2 = length;
            }
        }

        maxLength = Math.max(maxLength, max1 + max2);
        return Math.max(max1, max2) + 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.06 MB (Beats: 55.71%)

<br>
