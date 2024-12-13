# [LeetCode Records](../../README.md) - Question 1946 Largest Number After Mutating Substring

### Attempt 1: Use a while loop to reach the start index the substring and a while loop to change the characters
```java
class Solution {
    public String maximumNumber(String num, int[] change) {
        char[] arr = num.toCharArray();

        int i = 0;
        while (i < arr.length && change[arr[i] - '0'] <= arr[i] - '0') {
            i++;
        }

        while (i < arr.length && change[arr[i] - '0'] >= arr[i] - '0') {
            arr[i] = (char)(change[arr[i] - '0'] + '0');
            i++;
        }

        return new String(arr);
    }
}
```
- Runtime: 8 ms (Beats: 93.62%)
- Memory: 45.82 MB (Beats: 19.64%)

<br>
