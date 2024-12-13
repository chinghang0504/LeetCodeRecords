# [LeetCode Records](../../README.md) - Question 2168 Unique Substrings With Equal Digit Frequency

### Attempt 1: Use a HashSet to store the unique equal digit strings
```java
class Solution {
    public int equalDigitFrequency(String s) {
        char[] arr = s.toCharArray();
        Set<String> set = new HashSet<>();

        for (int i = 1; i <= arr.length; i++) {
            int[] counts = new int[10];
            for (int j = 0; j < i; j++) {
                counts[arr[j] - '0']++;
            }
            if (isEqualDigit(counts, counts[arr[0] - '0'])) {
                set.add(s.substring(0, i));
            }
            
            for (int j = i; j < arr.length; j++) {
                counts[arr[j] - '0']++;
                counts[arr[j - i] - '0']--;
                if (isEqualDigit(counts, counts[arr[j] - '0'])) {
                    set.add(s.substring(j - i + 1, j + 1));
                }
            }
        }

        return set.size();
    }

    private boolean isEqualDigit(int[] counts, int count) {
        for (int i = 0; i < 10; i++) {
            if (counts[i] != 0 && counts[i] != count) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 395 ms (Beats: 82.43%)
- Memory: 46.68 MB (Beats: 73.91%)

<br>
