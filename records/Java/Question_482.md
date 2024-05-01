# [LeetCode Records](../../README.md) - Question 482 License Key Formatting

### Attempt 1: Loop from back
```java
class Solution {
    public String licenseKeyFormatting(String s, int k) {
        StringBuilder stringBuilder = new StringBuilder();
        char[] arr = s.toCharArray();

        for (int i = arr.length - 1, count = 0; i >= 0; i--) {
            if (arr[i] != '-') {
                if (count == k) {
                    count = 0;
                    stringBuilder.append('-');
                }

                stringBuilder.append(Character.toUpperCase(arr[i]));
                count++;
            }
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 10 ms (Beats: 91.41%)
- Memory: 44.84 MB (Beats: 29.38%)

<br>
