# [LeetCode Records](../../README.md) - Question 547 Number of Provinces

### Attempt 1: Use DFS to search unreached cities and a boolean[] to track reached cities
```java
class Solution {

    private int n;
    private int[][] isConnected;
    private boolean[] reachedCities;

    public int findCircleNum(int[][] isConnected) {
        n = isConnected.length;
        this.isConnected = isConnected;
        reachedCities = new boolean[n];
        int numOfProvinces = 0;

        for (int i = 0; i < n; i++) {
            if (!reachedCities[i]) {
                numOfProvinces++;
                reachAllCitiesInTheSameProvince(i);
            }
        }

        return numOfProvinces;
    }

    private void reachAllCitiesInTheSameProvince(int city) {
        reachedCities[city] = true;
        for (int i = 0; i < n; i++) {
            if (!reachedCities[i] && isConnected[city][i] == 1) {
                reachAllCitiesInTheSameProvince(i);
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 48.03 MB (Beats: 37.40%)

<br>
