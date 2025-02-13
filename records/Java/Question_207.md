# [LeetCode Records](../../README.md) - Question 207 Course Schedule

### Attempt 1: Use an adjacency list to store the prerequisites in the graph. Use dfs to search the cycle. Use a boolean[] to store the course that has no cycle.
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
                int fromVertice = edge[0];
                int toVertice = edge[1];
                nodes[fromVertice] = new Node(toVertice, nodes[fromVertice]);
            }
        }
    }

    private Graph graph;
    private boolean[] checkedCourses;
    private boolean[] reachedCourses;

    public boolean canFinish(int numCourses, int[][] prerequisites) {
        graph = new Graph(numCourses, prerequisites);
        checkedCourses = new boolean[numCourses];
        reachedCourses = new boolean[numCourses];

        for (int i = 0; i < numCourses; i++) {
            if (hasCycle(i)) {
                return false;
            }
        }

        return true;
    }

    private boolean hasCycle(int course) {
        if (reachedCourses[course]) {
            return true;
        } else if (checkedCourses[course]) {
            return false;
        }
        reachedCourses[course] = true;
        checkedCourses[course] = true;

        Node node = graph.nodes[course];
        while (node != null) {
            if (hasCycle(node.vertice)) {
                return true;
            }

            node = node.next;
        }

        reachedCourses[course] = false;
        return false;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 44.36 MB (Beats: 99.75%)

<br>
