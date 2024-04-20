# [LeetCode Records](../README.md) - Question 128 Longest Consecutive Sequence

### Attempt 1: Use a HashSet to reocrd all numbers and loop for searching the next and the previous numbers
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> saved = new HashSet<>();
        for (int i : nums) {
            saved.add(i);
        }

        int max = 0;
        for (int i : nums) {
            if (!saved.contains(i)) {
                continue;
            }

            int count = 1;
            int target = i + 1;
            while (true) {
                if (!saved.contains(target)) {
                    break;
                }
                saved.remove(target);
                target++;
                count++;
            }
            target = i - 1;
            while (true) {
                if (!saved.contains(target)) {
                    break;
                }
                saved.remove(target);
                target--;
                count++;
            }

            max = Math.max(max, count);
        }

        return max;
    }
}
```
- Runtime: 34 ms (Beats: 50.16%)
- Memory: 62.07 MB (Beats: 57.52%)

<br>
