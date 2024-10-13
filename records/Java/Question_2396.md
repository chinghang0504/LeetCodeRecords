# [LeetCode Records](../../README.md) - Question 2396 Strictly Palindromic Number

### Attempt 1: Use a for loop to test every base
```java
class Solution {
    public boolean isStrictlyPalindromic(int n) {
        for (int i = 2; i <= n - 2; i++) {
            if (!isPalindromic(n, i)) {
                return false;
            }
        }

        return true;
    }

    private boolean isPalindromic(int n, int b) {
        List<Integer> list = new ArrayList<>();
        
        while (n >= b) {
            list.add(n % b);
            n /= b;
        }
        list.add(n);

        int size = list.size();
        for (int i = 0; i < size / 2; i++) {
            if (list.get(i) != list.get(size - i - 1)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.02 MB (Beats: 85.18%)

<br>
