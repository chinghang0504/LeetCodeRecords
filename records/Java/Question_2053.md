# [LeetCode Records](../../README.md) - Question 2053 Kth Distinct String in an Array

### Attempt 1: Use a HashMap to record the string counts
```java
class Solution {
    public String kthDistinct(String[] arr, int k) {
        Map<String, Integer> map = new HashMap<>();
        for (String str : arr) {
            map.merge(str, 1, Integer::sum);
        }

        int count = 0;
        for (String str : arr) {
            if (map.get(str) == 1) {
                count++;

                if (count == k) {
                    return str;
                }
            }
        }

        return "";
    }
}
```
- Runtime: 6 ms (Beats: 92.53%)
- Memory: 44.07 MB (Beats: 62.76%)

<br>
