# [LeetCode Records](../../README.md) - Question 1245 Tree Diameter

### Attempt 1: Use an adjacency list to store edges in the graph. Use depth-first search to get the maximum length.
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

        Graph(int n, int [][] edges) {
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
    private int maxLen;

    public int treeDiameter(int[][] edges) {
        int n = edges.length + 1;
        this.graph = new Graph(n, edges);
        this.maxLen = 0;

        getMaxLen(new boolean[n], 0);

        return maxLen;
    }

    private int getMaxLen(boolean[] reachedVertices, int vertice) {
        if (reachedVertices[vertice]) {
            return 0;
        } else {
            reachedVertices[vertice] = true;
        }

        int maxLen1 = 0;
        int maxLen2 = 0;
        Node node = graph.nodes[vertice];
        while (node != null) {
            int currMaxLen = getMaxLen(reachedVertices, node.vertice);
            if (currMaxLen >= maxLen1) {
                maxLen2 = maxLen1;
                maxLen1 = currMaxLen;
            } else if (currMaxLen > maxLen2) {
                maxLen2 = currMaxLen;
            }
            maxLen = Math.max(maxLen, maxLen1 + maxLen2);

            node = node.next;
        }

        return 1 + maxLen1;
    }
}
```
- Runtime: 4 ms (Beats: 99.38%)
- Memory: 46.06 MB (Beats: 84.16%)

<br>
