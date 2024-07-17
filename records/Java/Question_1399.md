# [LeetCode Records](../../README.md) - Question 1399 Count Largest Group

### Attempt 1: Save the counts of the sum of digits
```java
class Solution {
    public int countLargestGroup(int n) {
        int[] counts = new int[37];

        for (int i = 1; i <= n; i++) {
            int num = i;
            int sum = 0;
            while (num > 0) {
                sum += num % 10;
                num /= 10;
            }
            counts[sum]++;
        }

        int max = counts[0];
        int maxCount = 1;
        for (int i = 1; i < 37; i++) {
            if (counts[i] > max) {
                max = counts[i];
                maxCount = 1;
            } else if (counts[i] == max) {
                maxCount++;
            }
        }

        return maxCount;
    }
}
```
- Runtime: 3 ms (Beats: 92.92%)
- Memory: 39.90 MB (Beats: 99.38%)

<br>
