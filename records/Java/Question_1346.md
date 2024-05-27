# [LeetCode Records](../../README.md) - Question 1346 Check If N and Its Double Exist

### Attempt 1: Use a HashMap
```java
class Solution {
    public boolean checkIfExist(int[] arr) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int num : arr) {
            map.merge(num, 1, Integer::sum);
        }

        for (int num : arr) {
            int target = num * 2;
            if (target != num) {
                if (map.containsKey(target)) {
                    return true;
                }
            } else {
                if (map.get(num) > 1) {
                    return true;
                }
            }
        }

        return false;
    }
}
```
- Runtime: 4 ms (Beats: 16.49%)
- Memory: 43.80 MB (Beats: 8.98%)

<br>
