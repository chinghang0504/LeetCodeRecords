# [LeetCode Records](../../README.md) - Question 830 Positions of Large Groups

### Attempt 1: Use two if statements in a loop
```java
class Solution {
    public List<List<Integer>> largeGroupPositions(String s) {
        List<List<Integer>> result = new ArrayList<>();
        char[] arr = s.toCharArray();

        int start = 0;
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] != arr[start]) {
                if (i - start >= 3) {
                    result.add(Arrays.asList(start, i - 1));
                }
                start = i;
            }
        }
        if (arr.length - start >= 3) {
            result.add(Arrays.asList(start, arr.length - 1));
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 28.54%)
- Memory: 44.52 MB (Beats: 49.21%)

<br>

### Attempt 2: Remove an if statement inside the loop
```java
class Solution {
    public List<List<Integer>> largeGroupPositions(String s) {
        List<List<Integer>> result = new ArrayList<>();
        char[] arr = s.toCharArray();

        for (int i = 0, j = 1; i < arr.length ; i = j, j++) {
            while (j < arr.length && arr[j] == arr[i]) {
                j++;
            }
            if (j - i >= 3) {
                result.add(Arrays.asList(i, j - 1));
            }
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.30 MB (Beats: 80.45%)

<br>
