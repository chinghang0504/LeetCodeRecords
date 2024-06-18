# [LeetCode Records](../../README.md) - Question 2418 Sort the People

### Attempt 1: Use a HashMap and Arrays.sort()
```java
class Solution {
    public String[] sortPeople(String[] names, int[] heights) {
        int n = heights.length;
        Map<Integer, String> map = new HashMap<>();
        
        for (int i = 0; i < n; i++) {
            map.put(heights[i], names[i]);
        }

        Arrays.sort(heights);

        for (int i = 0; i < n; i++) {
            names[i] = map.get(heights[n - 1 - i]);
        }

        return names;
    }
}
```
- Runtime: 9 ms (Beats: 50.17%)
- Memory: 45.40 MB (Beats: 19.03%)

<br>
