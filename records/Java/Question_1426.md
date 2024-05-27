# [LeetCode Records](../../README.md) - Question 1426 Counting Elements

### Attempt 1: Use a HashSet
```java
class Solution {
    public int countElements(int[] arr) {
        Set<Integer> set = new HashSet<>();

        for (int num : arr) {
            set.add(num);
        }

        int count = 0;
        for (int num : arr) {
            if (set.contains(num + 1)) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 98.44%)
- Memory: 41.85 MB (Beats: 17.57%)

<br>
