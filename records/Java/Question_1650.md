# [LeetCode Records](../../README.md) - Question 1650 Lowest Common Ancestor of a Binary Tree III

### Attempt 1: Record all the parents of Node P
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node parent;
};
*/

class Solution {
    public Node lowestCommonAncestor(Node p, Node q) {
        Set<Node> set = new HashSet<>();
        set.add(p);

        Node parentNode = p.parent;
        while (parentNode != null) {
            set.add(parentNode);
            parentNode = parentNode.parent;
        }

        Node targetNode = q;
        while (targetNode != null) {
            if (set.contains(targetNode)) {
                return targetNode;
            }

            targetNode = targetNode.parent;
        }

        return null;
    }
}
```
- Runtime: 29 ms (Beats: 52.57%)
- Memory: 44.38 MB (Beats: 76.38%)

<br>

### Attempt 2: Record the parents of Node P and Node Q at the same time
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node parent;
};
*/

class Solution {
    public Node lowestCommonAncestor(Node p, Node q) {
        Set<Node> set = new HashSet<>();
        set.add(p);
        set.add(q);

        Node leftNode = p.parent;
        Node rightNode = q.parent;
        while (leftNode != null && rightNode != null) {
            if (set.contains(leftNode)) {
                return leftNode;
            } else {
                set.add(leftNode);
            }

            if (set.contains(rightNode)) {
                return rightNode;
            } else {
                set.add(rightNode);
            }

            leftNode = leftNode.parent;
            rightNode = rightNode.parent;
        }

        while (leftNode != null) {
            if (set.contains(leftNode)) {
                return leftNode;
            } else {
                set.add(leftNode);
            }

            leftNode = leftNode.parent;
        }

        while (rightNode != null) {
            if (set.contains(rightNode)) {
                return rightNode;
            } else {
                set.add(rightNode);
            }

            rightNode = rightNode.parent;
        }

        return null;
    }
}
```
- Runtime: 27 ms (Beats: 99.67%)
- Memory: 44.35 MB (Beats: 76.38%)

<br>
