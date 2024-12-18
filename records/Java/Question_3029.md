# [LeetCode Records](../../README.md) - Question 3029 Minimum Time to Revert Word to Initial State I

### Attempt 1: Compare the remaining characters in each loop
```java
class Solution {
    public int minimumTimeToInitialState(String word, int k) {
        char[] arr = word.toCharArray();

        int count = 0;
        boolean isEqual = false;
        for (int i = k; i < arr.length; i += k) {
            int len = arr.length - i;
            count++;
            isEqual = true;
            
            for (int j = 0; j < len; j++) {
                if (arr[i + j] != arr[j]) {
                    isEqual = false;
                    break;
                }
            }
            if (isEqual) {
                break;
            }
        }

        return isEqual ? count : count + 1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.98 MB (Beats: 90.48%)

<br>
