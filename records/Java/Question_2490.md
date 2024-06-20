# [LeetCode Records](../../README.md) - Question 2490 Circular Sentence

### Attempt 1: Use a loop
```java
class Solution {
    public boolean isCircularSentence(String sentence) {
        char[] arr = sentence.toCharArray();

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == ' ') {
                if (arr[i - 1] != arr[i + 1]) {
                    return false;
                }
            }
        }

        return arr[0] == arr[arr.length - 1];
    }
}
```
- Runtime: 1 ms (Beats: 99.10%)
- Memory: 42.00 MB (Beats: 42.64%)

<br>
