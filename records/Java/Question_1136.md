# [LeetCode Records](../../README.md) - Question 1136 Parallel Courses

### Attempt 1: Use an Adjacency list to store the directed edges
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

        int n;
        Node[] vertices;
        List<Integer> startVerticeList;

        Graph(int n, int[][] relations) {
            this.n = n;
            this.vertices = new Node[n];
            this.startVerticeList = new ArrayList<>();
            boolean[] toVertices = new boolean[n];

            for (int[] relation : relations) {
                int fromVertice = relation[0] - 1;
                int toVertice = relation[1] - 1;
                this.vertices[fromVertice] = new Node(toVertice, this.vertices[fromVertice]);
                toVertices[toVertice] = true;
            }

            for (int i = 0; i < n; i++) {
                if (!toVertices[i]) {
                    startVerticeList.add(i);
                }
            }
        }
    }

    public int minimumSemesters(int n, int[][] relations) {
        Graph graph = new Graph(n, relations);

        if (graph.startVerticeList.size() == 0) {
            return -1;
        }
        
        for (int startVectice : graph.startVerticeList) {
            if (hasCycle(startVectice, new boolean[n], graph)) {
                return -1;
            }
        }
        
        Set<Integer> reachedVertices = new HashSet<>();
        int[] lens = new int[n];
        int maxLen = 0;
        for (int startVectice : graph.startVerticeList) {
            int len = getLen(graph, reachedVertices, lens, startVectice);
            maxLen = Math.max(maxLen, len);
        }

        return reachedVertices.size() != n ? -1 : maxLen;
    }

    private boolean hasCycle(int vertice, boolean[] reachedVertices, Graph graph) {
        if (reachedVertices[vertice]) {
            return true;
        }
        reachedVertices[vertice] = true;

        Node node = graph.vertices[vertice];
        while (node != null) {
            if (hasCycle(graph.vertices[vertice].vertice, reachedVertices, graph)) {
                return true;
            }

            node = node.next;
        }

        reachedVertices[vertice] = false;
        return false;
    }

    private int getLen(Graph graph, Set<Integer> reachedVertices, int[] lens, int startVectice) {
        reachedVertices.add(startVectice);

        int len = 0;
        Node node = graph.vertices[startVectice];
        while (node != null) {
            if (reachedVertices.contains(node.vertice)) {
                len = Math.max(len, lens[node.vertice]);
            } else {
                len = Math.max(len, getLen(graph, reachedVertices, lens, node.vertice));
            }

            node = node.next;
        }

        lens[startVectice] = 1 + len;
        return lens[startVectice];
    }
}
```
- Runtime: 20 ms (Beats: 14.69%)
- Memory: 45.91 MB (Beats: 55.08%)

<br>
