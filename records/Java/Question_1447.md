# [LeetCode Records](../../README.md) - Question 1447 Simplified Fractions

### Attempt 1: Use a function to test if the fraction can be simplified
```java
class Solution {
    public List<String> simplifiedFractions(int n) {
        List<String> ans = new ArrayList<>();

        for (int i = 2; i <= n; i++) {
            for (int j = 1; j < i; j++) {
                if (isSimplified(j, i)) {
                    ans.add(j + "/" + i);
                }
            }
        }

        return ans;
    }

    private boolean isSimplified(int numerator, int denominator) {
        for (int i = 2; i <= numerator; i++) {
            if (numerator % i == 0 && denominator % i == 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 22 ms (Beats: 41.49%)
- Memory: 46.22 MB (Beats: 5.67%)

<br>
