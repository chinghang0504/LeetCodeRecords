# [LeetCode Records](../../README.md) - Question 3237 Alt and Tab Simulation

### Attempt 1: Use a HashMap to record the recent selected windows
```java
class Solution {
    public int[] simulationResult(int[] windows, int[] queries) {
        Map<Integer, Integer> map = new HashMap<>();

        int j = 0;
        for (int i = windows.length - 1; i >= 0; i--) {
            map.put(windows[i], j);
            j++;
        }

        for (int query : queries) {
            map.put(query, j);
            j++;
        }

        List<Map.Entry<Integer, Integer>> list = map.entrySet().stream()
            .sorted(Collections.reverseOrder(Map.Entry.comparingByValue()))
            .toList();
            
        int[] ans = new int[windows.length];
        int i = 0;
        for (Map.Entry<Integer, Integer> entry : list) {
            ans[i] = entry.getKey();
            i++;
        }

        return ans;
    }
}
```
- Runtime: 166 ms (Beats: 5.26%)
- Memory: 71.04 MB (Beats: 13.16%)

<br>
