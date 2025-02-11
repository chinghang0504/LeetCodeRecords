# [LeetCode Records](../../README.md) - Question 1462 Course Schedule IV

### Attempt 1: Use dfs to search the prerequisites
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
        Node[] nodes;

        Graph(int n, int[][] edges) {
            this.n = n;
            this.nodes = new Node[n];

            for (int i = 0; i < edges.length; i++) {
                int fromVertice = edges[i][0];
                int toVertice = edges[i][1];

                nodes[fromVertice] = new Node(toVertice, nodes[fromVertice]);
            }
        }
    }

    private Graph graph;

    public List<Boolean> checkIfPrerequisite(int numCourses, int[][] prerequisites, int[][] queries) {
        graph = new Graph(numCourses, prerequisites);

        List<Boolean> ans = new ArrayList<>();
        for (int[] query : queries) {
            ans.add(dfs(new boolean[numCourses], query[0], query[1]));
        }

        return ans;
    }

    private boolean dfs(boolean[] reachedVertices, int startVertice, int endVertice) {
        if (reachedVertices[startVertice]) {
            return false;
        } else if (startVertice == endVertice) {
            return true;
        } else {
            reachedVertices[startVertice] = true;
        }

        Node node = graph.nodes[startVertice];
        while (node != null) {
            if (dfs(reachedVertices, node.vertice, endVertice)) {
                return true;
            }

            node = node.next;
        }

        return false;
    }
}
```
- Runtime: 138 ms (Beats: 20.70%)
- Memory: 49.12 MB (Beats: 35.97%)

<br>
