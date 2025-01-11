# [LeetCode Records](../../README.md) - Question 133 Clone Graph

### Attempt 1: Use a HashMap to store the node value and cloned node key-value pairs
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;
    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}
*/

class Solution {

    private Map<Integer, Node> valToclonedNodeMap;

    public Node cloneGraph(Node node) {
        if (node == null) {
            return null;
        }

        valToclonedNodeMap = new HashMap<>();

        return cloneGraphRecursion(node);
    }

    private Node cloneGraphRecursion(Node node) {
        Node clonedNode = valToclonedNodeMap.get(node.val);
        if (clonedNode != null) {
            return clonedNode;
        }

        clonedNode = new Node(node.val);
        valToclonedNodeMap.put(node.val, clonedNode);
        for (Node nodeChild : node.neighbors) {
            clonedNode.neighbors.add(cloneGraphRecursion(nodeChild));
        }

        return clonedNode;
    }
}
```
- Runtime: 25 ms (Beats: 69.42%)
- Memory: 42.74 MB (Beats: 64.51%)

<br>

### Attempt 2: Use a HashMap to store the node and cloned node key-value pairs
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;
    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}
*/

class Solution {

    private Map<Node, Node> valToclonedNodeMap;

    public Node cloneGraph(Node node) {
        if (node == null) {
            return null;
        }

        valToclonedNodeMap = new HashMap<>();

        return cloneGraphRecursion(node);
    }

    private Node cloneGraphRecursion(Node node) {
        Node clonedNode = valToclonedNodeMap.get(node);
        if (clonedNode != null) {
            return clonedNode;
        }

        clonedNode = new Node(node.val);
        valToclonedNodeMap.put(node, clonedNode);
        for (Node nodeChild : node.neighbors) {
            clonedNode.neighbors.add(cloneGraphRecursion(nodeChild));
        }

        return clonedNode;
    }
}
```
- Runtime: 24 ms (Beats: 89.61%)
- Memory: 42.83 MB (Beats: 47.21%)

<br>
