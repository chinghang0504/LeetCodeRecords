# [LeetCode Records](../../README.md) - Question 2496 Maximum Value of a String in an Array

### Attempt 1: Use Integer.valueOf()
```java
class Solution {
    public int maximumValue(String[] strs) {
        int max = 0;

        for (String str : strs) {
            int val;
            try {
                val = Integer.valueOf(str);
            } catch (Exception e) {
                val = str.length();
            }

            max = Math.max(max, val);
        }

        return max;
    }
}
```
- Runtime: 2 ms (Beats: 38.77%)
- Memory: 41.90 MB (Beats: 18.35%)

<br>
