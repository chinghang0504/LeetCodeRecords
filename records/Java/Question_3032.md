# [LeetCode Records](../../README.md) - Question 3032 Count Numbers With Unique Digits II

### Attempt 1: Use a loop with a HashSet
```java
class Solution {
    public int numberCount(int a, int b) {
        int count = 0;

        for (int i = a; i <= b; i++) {
            Set<Integer> set = new HashSet<>();
            int n = i;
            boolean isUnique = true;

            while (n > 0) {
                if (set.contains(n % 10)) {
                    isUnique = false;
                    break;
                }

                set.add(n % 10);
                n /= 10;
            }

            if (isUnique) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 13 ms (Beats: 35.56%)
- Memory: 44.29 MB (Beats: 59.44%)

<br>
