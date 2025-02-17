# [LeetCode Records](../../README.md) - Question 1042 Flower Planting With No Adjacent

### Attempt 1: Use an adjacency list to store the edges in the graph. Check every neighbour's type.
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
                int vertice1 = edge[0] - 1;
                int vertice2 = edge[1] - 1;
                nodes[vertice1] = new Node(vertice2, nodes[vertice1]);
                nodes[vertice2] = new Node(vertice1, nodes[vertice2]);
            }
        }
    }

    private Graph graph;

    public int[] gardenNoAdj(int n, int[][] paths) {
        graph = new Graph(n, paths);

        int[] ans = new int[n];
        for (int i = 0; i < n; i++) {
            Node node = graph.nodes[i];
            boolean[] types = new boolean[4];
            
            while (node != null) {
                int type = ans[node.vertice];
                if (type != 0) {
                    types[type - 1] = true;
                }
                node = node.next;
            }

            for (int j = 0; j < 4; j++) {
                if (!types[j]) {
                    ans[i] = j + 1;
                    break;
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 11 ms (Beats: 95.63%)
- Memory: 53.16 MB (Beats: 53.75%)

<br>
