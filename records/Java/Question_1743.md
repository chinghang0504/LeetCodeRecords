# [LeetCode Records](../../README.md) - Question 

### Attempt 1: Use a HashMap to store the edges
```java
class Solution {
    public int[] restoreArray(int[][] adjacentPairs) {
        Map<Integer, Integer[]> edgeMap = new HashMap<>();
        for (int[] adjacentPair : adjacentPairs) {
            updateEdgeMap(edgeMap, adjacentPair[0], adjacentPair[1]);
            updateEdgeMap(edgeMap, adjacentPair[1], adjacentPair[0]);
        }

        int head = 0;
        for (Map.Entry<Integer, Integer[]> entry : edgeMap.entrySet()) {
            if (entry.getValue()[1] == Integer.MIN_VALUE) {
                head = entry.getKey();
                break;
            }
        }

        int[] ans = new int[adjacentPairs.length + 1];
        ans[0] = head;
        ans[1] = edgeMap.get(head)[0];
        for (int i = 2; i < adjacentPairs.length + 1; i++) {
            Integer[] arr = edgeMap.get(ans[i - 1]);
            ans[i] = arr[0] != ans[i - 2] ? arr[0] : arr[1];
        }

        return ans;
    }

    private void updateEdgeMap(Map<Integer, Integer[]> edgeMap, int key, int value) {
        Integer[] arr = edgeMap.get(key);
        if (arr == null) {
            arr = new Integer[2];
            arr[0] = value;
            arr[1] = Integer.MIN_VALUE;
            edgeMap.put(key, arr);
        } else {
            arr[1] = value;
        }
    }
}
```
- Runtime: 46 ms (Beats: 98.77%)
- Memory: 92.75 MB (Beats: 64.45%)

<br>
