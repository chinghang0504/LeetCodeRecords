# [LeetCode Records](../../README.md) - Question 1319 Number of Operations to Make Network Connected

### Attempt 1: Count the number of components in the graph. Use depth-first search to search unvisited vertices in the same components.
```java
class Solution {

    class Node {

        int vertice;
        Node next;

        Node(int vertice, Node next) {
            this.vertice = vertice;
            this.next = next;
        }
    }

    class Graph {

        Node[] nodes;

        Graph(int n, int[][] edges) {
            nodes = new Node[n];
            
            for (int[] edge : edges) {
                int vertice1 = edge[0];
                int vertice2 = edge[1];
                nodes[vertice1] = new Node(vertice2, nodes[vertice1]);
                nodes[vertice2] = new Node(vertice1, nodes[vertice2]);
            }
        }
    }

    private Graph graph;
    private boolean[] visitedVertices;

    public int makeConnected(int n, int[][] connections) {
        if (connections.length < n - 1) {
            return -1;
        }

        graph = new Graph(n, connections);
        visitedVertices = new boolean[n];

        int numOfComponents = 0;
        for (int i = 0; i < n; i++) {
            if (!visitedVertices[i]) {
                dfs(i);
                numOfComponents++;
            }
        }

        return numOfComponents - 1;
    }

    private void dfs(int vertice) {
        if (visitedVertices[vertice]) {
            return;
        } else {
            visitedVertices[vertice] = true;
        }

        Node node = graph.nodes[vertice];
        while (node != null) {
            dfs(node.vertice);
            node = node.next;
        }
    }
}
```
- Runtime: 9 ms (Beats: 52.15%)
- Memory: 65.79 MB (Beats: 35.65%)

<br>
