# [LeetCode Records](../../README.md) - Question 2192 All Ancestors of a Node in a Directed Acyclic Graph

### Attempt 1: Use dfs to find all ancestors
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
            nodes = new Node[n];

            for (int[] edge : edges) {
                int fromVertice = edge[0];
                int toVertice = edge[1];
                nodes[toVertice] = new Node(fromVertice, nodes[toVertice]);
            }
        }
    }

    private Graph graph;

    public List<List<Integer>> getAncestors(int n, int[][] edges) {
        graph = new Graph(n, edges);
        List<List<Integer>> ans = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            Set<Integer> set = new HashSet<>();
            getAllAncestorsFromCurr(set, i);
            set.remove(i);

            List<Integer> list = new ArrayList<>(set);
            list.sort(null);
            ans.add(list);
        }

        return ans;
    }

    private void getAllAncestorsFromCurr(Set<Integer> set, int curr) {
        if (set.contains(curr)) {
            return;
        } else {
            set.add(curr);
        }

        Node node = graph.nodes[curr];
        while (node != null) {
            getAllAncestorsFromCurr(set, node.vertice);
            node = node.next;
        }
    }
}
```
- Runtime: 77 ms (Beats: 66.67%)
- Memory: 67.08 MB (Beats: 51.81%)

<br>
