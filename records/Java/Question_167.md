# [LeetCode Records](../../README.md) - Question 167 Two Sum II - Input Array Is Sorted

### Attempt 1: Use a HashMap to store the number and the index key-value pairs
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = numbers.length - 1; i >= 0; i--) {
            int nextTarget = target - numbers[i];
            if (nextTarget >= numbers[i]) {
                Integer index = map.get(nextTarget);
                if (index != null) {
                    return new int[]{ i + 1, index + 1 };
                }
            }

            map.put(numbers[i], i);
        }

        return null;
    }
}
```
- Runtime: 4 ms (Beats: 20.73%)
- Memory: 46.51 MB (Beats: 93.60%)

<br>
