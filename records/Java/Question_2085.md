# [LeetCode Records](../../README.md) - Question 2085 Count Common Words With One Occurrence

### Attempt 1: Use two HashMap
```java
class Solution {
    public int countWords(String[] words1, String[] words2) {
        Map<String, Integer> map1 = new HashMap<>();
        Map<String, Integer> map2 = new HashMap<>();

        for (String str : words1) {
            map1.merge(str, 1, Integer::sum);
        }
        for (String str : words2) {
            map2.merge(str, 1, Integer::sum);
        }

        int count = 0;
        for (String key : map1.keySet()) {
            if (map1.get(key) == 1) {
                Integer val = map2.get(key);
                if (val != null && val == 1) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 86.85%)
- Memory: 44.00 MB (Beats: 75.97%)

<br>
