# [LeetCode Records](../../README.md) - Question 258 Add Digits

### Attempt 1: 
```java
class Solution {
    public int addDigits(int num) {
        int sum = 0;
        
        while (true) {
            sum = 0;

            while (num > 9) {
                sum += num % 10;
                num /= 10;
            }
            sum += num;

            if (sum < 10) {
                break;
            } else {
                num = sum;
            }
        }
        
        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.75 MB (Beats: 54.57%)

<br>
