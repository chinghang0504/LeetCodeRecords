# [LeetCode Records](../../README.md) - Question 

### Attempt 1: Use an int[] to store the status of nodes
```java
class Solution {
    public List<Integer> eventualSafeNodes(int[][] graph) {
        int[] status = new int[graph.length];
        
        for (int i = 0; i < graph.length; i++) {
            searchNode(graph, status, i);
        }

        List<Integer> ans = new ArrayList<>();
        for (int i = 0; i < graph.length; i++) {
            if (status[i] == 2) {
                ans.add(i);
            }
        }
        
        return ans;
    }

    private void searchNode(int[][] graph, int[] status, int start) {
        if (status[start] != 0) {
            return;
        } else if (graph[start].length == 0) {
            status[start] = 2;
            return;
        }

        status[start] = 1;
        boolean isAllToTerminal = true;
        for (int end : graph[start]) {
            searchNode(graph, status, end);
            if (status[end] != 2) {
                isAllToTerminal = false;
                break;
            }
        }

        if (isAllToTerminal) {
            status[start] = 2;
        }
    }
}
```
- Runtime: 4 ms (Beats: 98.83%)
- Memory: 55.26 MB (Beats: 76.20%)

<br>
