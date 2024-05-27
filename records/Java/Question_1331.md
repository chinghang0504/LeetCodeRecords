# [LeetCode Records](../../README.md) - Question 1331 Rank Transform of an Array

### Attempt 1: Use an int[] and a HashMap
```java
class Solution {
    public int[] arrayRankTransform(int[] arr) {
        int[] sortedArr = arr.clone();
        Arrays.sort(sortedArr);

        Map<Integer, Integer> map = new HashMap<>();
        int currRank = 1;
        for (int i = 0; i < arr.length; i++) {
            if (!map.containsKey(sortedArr[i])) {
                map.put(sortedArr[i], currRank);
                currRank++;
            }
        }

        int[] result = new int[arr.length];
        for (int i = 0; i < arr.length; i++) {
            result[i] = map.get(arr[i]);
        }

        return result;
    }
}
```
- Runtime: 23 ms (Beats: 94.01%)
- Memory: 62.56 MB (Beats: 21.33%)

<br>
