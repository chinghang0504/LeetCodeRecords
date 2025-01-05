# [LeetCode Records](../../README.md) - Question 1506 Find Root of N-Ary Tree

### Attempt 1: Use a HashSet to store the child nodes
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
    public Node findRoot(List<Node> tree) {
        Set<Node> childrenSet = new HashSet<>();
        for (Node node : tree) {
            for (Node child : node.children) {
                childrenSet.add(child);
            }
        }

        for (Node node : tree) {
            if (!childrenSet.contains(node)) {
                return node;
            }
        }

        return null;
    }
}
```
- Runtime: 17 ms (Beats: 51.30%)
- Memory: 50.04 MB (Beats: 67.83%)

<br>

### Attempt 2: Use the sum of all node values
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
    public Node findRoot(List<Node> tree) {
        int nodeSum = 0;
        int childSum = 0;
        for (Node node : tree) {
            nodeSum += node.val;

            for (Node child : node.children) {
                childSum += child.val;
            }
        }

        int targetVal = nodeSum - childSum;
        for (Node node : tree) {
            if (node.val == targetVal) {
                return node;
            }
        }

        return null;
    }
}
```
- Runtime: 12 ms (Beats: 97.39%)
- Memory: 50.20 MB (Beats: 52.17%)

<br>
