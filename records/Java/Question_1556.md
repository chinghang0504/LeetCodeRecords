# [LeetCode Records](../../README.md) - Question 1556 Thousand Separator

### Attempt 1: 
```java
class Solution {
    public String thousandSeparator(int n) {
        if (n == 0) {
            return "0";
        }

        int count = 0;
        StringBuilder stringBuilder = new StringBuilder();

        while (n > 0) {
            if (count == 3) {
                stringBuilder.append('.');
                count = 0;
            }

            stringBuilder.append(n % 10);
            n /= 10;
            count++;
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.57 MB (Beats: 72.43%)

<br>
