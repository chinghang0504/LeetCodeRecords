# [LeetCode Records](../../README.md) - Question 2870 Minimum Number of Operations to Make Array Empty

### Attempt 1: Use a HashMap to store the number and the count key-value pairs
```java
class Solution {
    public int minOperations(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.merge(num, 1, Integer::sum);
        }

        int numOfOperations = 0;
        for (int count : map.values()) {
            if (count == 1) {
                return -1;
            } else {
                numOfOperations += count % 3 == 0 ? count / 3 : count / 3 + 1;
            }
        }

        return numOfOperations;
    }
}
```
- Runtime: 18 ms (Beats: 90.57%)
- Memory: 58.58 MB (Beats: 71.91%)

<br>
