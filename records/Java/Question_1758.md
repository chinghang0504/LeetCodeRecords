# [LeetCode Records](../../README.md) - Question 1758 Minimum Changes To Make Alternating Binary String

### Attempt 1: Count the string start from '0' and the string start from '1'
```java
class Solution {
    public int minOperations(String s) {
        char[] arr = s.toCharArray();

        int count1 = 0;
        for (int i = 0; i < arr.length; i++) {
            if (i % 2 == 0) {
                if (arr[i] != '0') {
                    count1++;
                }
            } else {
                if (arr[i] != '1') {
                    count1++;
                }
            }
        }

        int count2 = 0;
        for (int i = 0; i < arr.length; i++) {
            if (i % 2 == 0) {
                if (arr[i] != '1') {
                    count2++;
                }
            } else {
                if (arr[i] != '0') {
                    count2++;
                }
            }
        }

        return Math.min(count1, count2);
    }
}
```
- Runtime: 3 ms (Beats: 90.34%)
- Memory: 42.53 MB (Beats: 21.07%)

<br>
