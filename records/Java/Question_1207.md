# [LeetCode Records](../../README.md) - Question 1207 Unique Number of Occurrences

### Attempt 1: Use a HashMap and a HashSet
```java
class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : arr) {
            map.merge(num, 1, Integer::sum);
        }

        Set<Integer> set = new HashSet<>();
        for (int num : map.values()) {
            if (set.contains(num)) {
                return false;
            } else {
                set.add(num);
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 96.02%)
- Memory: 42.48 MB (Beats: 5.01%)

<br>
