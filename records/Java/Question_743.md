# [LeetCode Records](../../README.md) - Question 743 Network Delay Time

### Attempt 1: Use an adjacency list to store the edges in the graph. Use depth-first search to get the minimum delay time of each vertice.
```java
class Solution {

    class Node {

        int vertice;
        int time;
        Node next;

        Node (int vertice, int time, Node next) {
            this.vertice = vertice;
            this.time = time;
            this.next = next;
        }
    }

    class Graph {

        Node[] nodes;

        Graph(int n, int[][] edges) {
            this.nodes = new Node[n];

            for (int[] edge : edges) {
                int fromVertice = edge[0] - 1;
                int toVertice = edge[1] - 1;
                int time = edge[2];
                nodes[fromVertice] = new Node(toVertice, time, nodes[fromVertice]);
            }
        }
    }

    private Graph graph;
    private Integer[] minTimes;

    public int networkDelayTime(int[][] times, int n, int k) {
        this.graph = new Graph(n, times);
        this.minTimes = new Integer[n];

        updateDelayTime(k - 1, 0);

        int maxTime = 0;
        for (int i = 0; i < n; i++) {
            if (minTimes[i] == null) {
                return -1;
            }

            maxTime = Math.max(maxTime, minTimes[i]);
        }

        return maxTime;
    }

    private void updateDelayTime(int vertice, int delayTime) {
        if (this.minTimes[vertice] != null && delayTime >= this.minTimes[vertice]) {
            return;
        }
        this.minTimes[vertice] = delayTime;

        Node node = this.graph.nodes[vertice];
        while (node != null) {
            updateDelayTime(node.vertice, delayTime + node.time);
            node = node.next;
        }
    }
}
```
- Runtime: 173 ms (Beats: 5.13%)
- Memory: 47.16 MB (Beats: 91.74%)

<br>

### Attempt 2: Use an adjacency list to store the edges in the graph. Use breadth-first search to get the minimum delay time of each vertice.
```java
class Solution {

    class Node {

        int vertice;
        int time;
        Node next;

        Node (int vertice, int time, Node next) {
            this.vertice = vertice;
            this.time = time;
            this.next = next;
        }
    }

    class Graph {

        Node[] nodes;

        Graph(int n, int[][] edges) {
            this.nodes = new Node[n];

            for (int[] edge : edges) {
                int fromVertice = edge[0] - 1;
                int toVertice = edge[1] - 1;
                int time = edge[2];
                nodes[fromVertice] = new Node(toVertice, time, nodes[fromVertice]);
            }
        }
    }

    private Graph graph;
    private Integer[] minTimes;

    public int networkDelayTime(int[][] times, int n, int k) {
        this.graph = new Graph(n, times);
        this.minTimes = new Integer[n];

        updateDelayTime(k - 1);

        int maxTime = 0;
        for (int i = 0; i < n; i++) {
            if (minTimes[i] == null) {
                return -1;
            }

            maxTime = Math.max(maxTime, minTimes[i]);
        }

        return maxTime;
    }

    private void updateDelayTime(int vertice) {
        Set<Integer> set = new HashSet<>();
        set.add(vertice);
        this.minTimes[vertice] = 0;

        while (!set.isEmpty()) {
            Set<Integer> nextSet = new HashSet<>();

            for (int currVertice : set) {
                int currDelayTime = this.minTimes[currVertice];
                Node node = this.graph.nodes[currVertice];
                while (node != null) {
                    int nextDelayTime = currDelayTime + node.time;
                    if (this.minTimes[node.vertice] == null || nextDelayTime < this.minTimes[node.vertice]) {
                        this.minTimes[node.vertice] = nextDelayTime;
                        nextSet.add(node.vertice);
                    }

                    node = node.next;
                }
            }

            set = nextSet;
        }
    }
}
```
- Runtime: 10 ms (Beats: 86.02%)
- Memory: 45.77 MB (Beats: 99.55%)

<br>
