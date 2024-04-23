# [LeetCode Records](../README.md) - Question 293 Flip Game

### Attempt 1: Loop for checking two consecutive "++"
```java
class Solution {
    public List<String> generatePossibleNextMoves(String currentState) {
        List<String> result = new ArrayList<>();
        char[] arr = currentState.toCharArray();

        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] == '+' && arr[i + 1] == '+') {
                char[] copyArr = arr.clone();
                copyArr[i] = '-';
                copyArr[i + 1] = '-';
                result.add(new String(copyArr));
            }
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.79 MB (Beats: 34.87%)

<br>
