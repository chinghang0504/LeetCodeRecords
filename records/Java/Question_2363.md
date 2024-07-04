# [LeetCode Records](../../README.md) - Question 2363 Merge Similar Items

### Attempt 1: Use an int[] to calculate the sum of weights
```java
class Solution {
    public List<List<Integer>> mergeSimilarItems(int[][] items1, int[][] items2) {
        int[] weights = new int[1001];
        
        for (int[] item : items1) {
            weights[item[0]] += item[1];
        }
        for (int[] item : items2) {
            weights[item[0]] += item[1];
        }

        List<List<Integer>> ret = new ArrayList<>();
        for (int i = 1; i < 1001; i++) {
            if (weights[i] > 0) {
                ret.add(List.of(i, weights[i]));
            }
        }

        return ret;
    }
}
```
- Runtime: 3 ms (Beats: 94.18%)
- Memory: 45.20 MB (Beats: 85.01%)

<br>
