# [LeetCode Records](../../README.md) - Question 2404 Most Frequent Even Element

### Attempt 1: Use an int[] to save the number counts and a HashSet to save the maximum count numbers
```java
class Solution {
    public int mostFrequentEven(int[] nums) {
        int[] counts = new int[100001];
        int maxCount = 0;
        Set<Integer> set = null;

        for (int num : nums) {
            if (num % 2 == 1) {
                continue;
            }

            counts[num]++;
            if (counts[num] > maxCount) {
                maxCount = counts[num];
                set = new HashSet<>();
                set.add(num);
            } else if (counts[num] == maxCount) {
                set.add(num);
            }
        }

        if (maxCount == 0) {
            return -1;
        }

        int min = Integer.MAX_VALUE;
        for (int num : set) {
            min = Math.min(min, num);
        }

        return min;
    }
}
```
- Runtime: 10 ms (Beats: 93.22%)
- Memory: 44.71 MB (Beats: 70.73%)

<br>
