# [LeetCode Records](../../README.md) - Question 1925 Count Square Sum Triples

### Attempt 1: 
```java
class Solution {
    public int countTriples(int n) {
        int count = 0;

        for (int i = 1; i <= n; i++) {
            int firstSquare = i * i;
            for (int j = 1; j <= n; j++) {
                int secondSquare = j * j;
                int firstSum = firstSquare + secondSquare;
                for (int k = 1; k <= n; k++) {
                    int thirdSquare = k * k;

                    if (firstSum == thirdSquare) {
                        count++;
                    }
                }
            }
        }

        return count;
    }
}
```
- Runtime: 339 ms (Beats: 26.26%)
- Memory: 40.88 MB (Beats: 12.85%)

<br>
