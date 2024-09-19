# [LeetCode Records](../../README.md) - Question 3167 Better Compression of String

### Attempt 1: Get the character and its count in each iteration
```java
class Solution {
    public String betterCompression(String compressed) {
        int[] counts = new int[26];
        char[] arr = compressed.toCharArray();
        
        int i = 0;
        while (i < arr.length) {
            char target = arr[i];
            i++;

            int count = 0;
            while (i < arr.length && Character.isDigit(arr[i])) {
                count = count * 10 + arr[i] - '0';
                i++;
            }
            counts[target - 'a'] += count;
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int j = 0; j < 26; j++) {
            if (counts[j] > 0) {
                stringBuilder.append((char)('a' + j));
                stringBuilder.append(counts[j]);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 8 ms (Beats: 87.42%)
- Memory: 45.33 MB (Beats: 57.53%)

<br>
