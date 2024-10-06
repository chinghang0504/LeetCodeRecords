# [LeetCode Records](../../README.md) - Question 1753 Maximum Score From Removing Stones

### Attempt 1: Use Arrays.sort() to sort the array after each take
```java
class Solution {
    public int maximumScore(int a, int b, int c) {
        int[] arr = { a, b, c };
        Arrays.sort(arr);

        int count = 0;
        while (arr[1] != 0 && arr[2] != 0) {
            arr[1]--;
            arr[2]--;
            Arrays.sort(arr);
            count++;
        } 

        return count;
    }
}
```
- Runtime: 17 ms (Beats: 53.46%)
- Memory: 40.51 MB (Beats: 67.69%)

<br>
