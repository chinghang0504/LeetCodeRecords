# [LeetCode Records](../../README.md) - Question 3216 Lexicographically Smallest String After a Swap

### Attempt 1: Use a for loop to the same parity
```java
class Solution {
    public String getSmallestString(String s) {
        char[] arr = s.toCharArray();

        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] % 2 == arr[i + 1] % 2 && arr[i] > arr[i + 1]) {
                char temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                break;
            }
        }

        return new String(arr);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.80 MB (Beats: 68.12%)

<br>
