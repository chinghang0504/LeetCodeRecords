# [LeetCode Records](../../README.md) - Question 961 N-Repeated Element in Size 2N Array

### Attempt 1: Use a HashMap to save the counts
```java
class Solution {
    public int repeatedNTimes(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.merge(num, 1, Integer::sum);
        }

        return map.entrySet().stream()
                .filter(x -> x.getValue() == nums.length / 2)
                .findFirst().get()
                .getKey();
    }
}
```
- Runtime: 16 ms (Beats: 29.36%)
- Memory: 44.58 MB (Beats: 96.60%)

<br>

### Attempt 2: Use an int[] to save the counts
```java
class Solution {
    public int repeatedNTimes(int[] nums) {
        int n = nums.length / 2;
        int[] counts = new int[10000];
        
        for (int num : nums) {
            counts[num]++;
            if (counts[num] == n) {
                return num;
            }
        }
        
        return -1;
    }
}
```
- Runtime: 3 ms (Beats: 46.73%)
- Memory: 45.48 MB (Beats: 12.09%)

<br>
