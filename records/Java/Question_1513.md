# [LeetCode Records](../../README.md) - Question 1513 Number of Substrings With Only 1s

### Attempt 1: Count the number of consecutive 1s
```java
class Solution {
    public int numSub(String s) {
        char[] arr = s.toCharArray();
        long sum = 0;
        
        long count = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == '1') {
                count++;
            } else {
                sum += (1 + count) * count / 2;
                count = 0;
            }
        }
        sum += (1 + count) * count / 2;

        return (int)(sum % 1_000_000_007L);
    }
}
```
- Runtime: 3 ms (Beats: 99.39%)
- Memory: 44.39 MB (Beats: 75.98%)

<br>
