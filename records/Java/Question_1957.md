# [LeetCode Records](../../README.md) - Question 1957 Delete Characters to Make Fancy String

### Attempt 1: Use two variables to record the previous characters
```java
class Solution {
    public String makeFancyString(String s) {
        if (s.length() <= 2) {
            return s;
        }

        char[] arr = s.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();
        
        char prev1 = arr[0];
        char prev2 = arr[1];
        stringBuilder.append(prev1);
        stringBuilder.append(prev2);
        for (int i = 2; i < arr.length; i++) {
            if (prev1 == arr[i] && prev2 == arr[i]) {
                continue;
            }

            stringBuilder.append(arr[i]);
            prev1 = prev2;
            prev2 = arr[i];
        }
        
        return stringBuilder.toString();
    }
}
```
- Runtime: 23 ms (Beats: 97.11%)
- Memory: 45.50 MB (Beats: 66.67%)

<br>
