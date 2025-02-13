# [LeetCode Records](../../README.md) - Question 785 Is Graph Bipartite?

### Attempt 1: Use depth-first search to determine whether vertices in the corresponding sets
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

        Graph(int[][] toVectices) {
            this.nodes = new Node[toVectices.length];

            for (int i = 0; i < toVectices.length; i++) {
                int fromVertice = i;

                for (int toVertice : toVectices[i]) {
                    nodes[fromVertice] = new Node(toVertice, nodes[fromVertice]);
                }
            }
        }
    }

    private Graph graph;
    private Set<Integer> set1;
    private Set<Integer> set2;

    public boolean isBipartite(int[][] graph) {
        this.graph = new Graph(graph);
        this.set1 = new HashSet<>();
        this.set2 = new HashSet<>();

        for (int i = 0; i < graph.length; i++) {
            if (!set1.contains(i) && !set2.contains(i) && !dfs(i, true)) {
                return false;
            }
        }

        return true;
    }

    private boolean dfs(int vertice, boolean isSet1) {
        if (isSet1) {
            if (set1.contains(vertice)) {
                return true;
            } else if (set2.contains(vertice)) {
                return false;
            } else {
                set1.add(vertice);
            }
        } else {
            if (set1.contains(vertice)) {
                return false;
            } else if (set2.contains(vertice)) {
                return true;
            } else {
                set2.add(vertice);
            }
        }

        Node node = graph.nodes[vertice];
        while (node != null) {
            if (!dfs(node.vertice, !isSet1)) {
                return false;
            }
            node = node.next;
        }

        return true;
    }
}
```
- Runtime: 5 ms (Beats: 16.87%)
- Memory: 45.01 MB (Beats: 64.26%)

<br>
