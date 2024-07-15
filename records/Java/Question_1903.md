# [LeetCode Records](../../README.md) - Question 1903 Largest Odd Number in String

### Attempt 1: Use toCharArray()
```java
class Solution {
    public String largestOddNumber(String num) {
        char[] arr = num.toCharArray();

        int index = -1;
        for (int i = arr.length - 1; i >= 0; i--) {
            if (arr[i] % 2 == 1) {
                index = i;
                break;
            }
        }

        return num.substring(0, index + 1);
    }
}
```
- Runtime: 2 ms (Beats: 36.51%)
- Memory: 45.66 MB (Beats: 11.55%)

<br>

### Attempt 2: Use charAt()
```java
class Solution {
    public String largestOddNumber(String num) {
        int size = num.length();

        int index = -1;
        for (int i = size - 1; i >= 0; i--) {
            if (num.charAt(i) % 2 == 1) {
                index = i;
                break;
            }
        }

        return num.substring(0, index + 1);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.45 MB (Beats: 23.80%)

<br>
