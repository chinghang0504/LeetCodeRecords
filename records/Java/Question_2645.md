# [LeetCode Records](../../README.md) - Question 2645 Minimum Additions to Make Valid String

### Attempt 1: Compare the first character, the last character and Compare the previous character in the for loop
```java
class Solution {
    public int addMinimum(String word) {
        char[] arr = word.toCharArray();

        int count = 0;
        char firstCh = arr[0];
        if (firstCh == 'b') {
            count++;
        } else if (firstCh == 'c') {
            count += 2;
        }

        for (int i = 1; i < arr.length; i++) {
            if (arr[i - 1] == arr[i]) {
                count += 2;
            } else if (arr[i] - arr[i - 1] == 2 || arr[i - 1] - arr[i] == 1) {
                count++;
            }
        }

        char lastCh = arr[arr.length - 1];
        if (lastCh == 'a') {
            count += 2;
        } else if (lastCh == 'b') {
            count++;
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.62 MB (Beats: 60.58%)

<br>
