# [LeetCode Records](../../README.md) - Question 1256 Encode Number

### Attempt 1: Use the formula (num - 1) % 2 and (num - 1) / 2
```java
class Solution {
    public String encode(int num) {
        if (num == 0) {
            return "";
        }

        StringBuilder stringBuilder = new StringBuilder();

        while (num > 0) {
            char ch = (num - 1) % 2 == 0 ? '0' : '1';
            stringBuilder.append(ch);
            num = (num - 1) / 2;
        }
        
        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.00 MB (Beats: 46.67%)

<br>
