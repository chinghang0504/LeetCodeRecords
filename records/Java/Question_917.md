# [LeetCode Records](../../README.md) - Question 917 Reverse Only Letters

### Attempt 1: 
```java
class Solution {
    public String reverseOnlyLetters(String s) {
        char[] arr = s.toCharArray();

        int i = 0, j = arr.length - 1;
        while (i < j) {
            while (i < arr.length && !Character.isLetter(arr[i])) {
                i++;
            }
            while (j >= 0 && !Character.isLetter(arr[j])) {
                j--;
            }

            if (i >= j) {
                break;
            }

            char temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;

            i++;
            j--;
        }

        return new String(arr);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.25 MB (Beats: 79.43%)

<br>
