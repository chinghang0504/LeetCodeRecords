# [LeetCode Records](../../README.md) - Question 2295 Replace Elements in an Array

### Attempt 1: Use a HashMap to store the number and its index key-value pairs
```java
class Solution {
    public int[] arrayChange(int[] nums, int[][] operations) {
        Map<Integer, Integer> numToIndexMap = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            numToIndexMap.put(nums[i], i);
        }

        for (int[] operation : operations) {
            int index = numToIndexMap.get(operation[0]);
            nums[index] = operation[1];
            numToIndexMap.put(operation[1], index);
        }

        return nums;
    }
}
```
- Runtime: 35 ms (Beats: 89.90%)
- Memory: 95.53 MB (Beats: 5.29%)

<br>

### Attempt 2: Use an int[] to store the number and its index
```java
class Solution {
    public int[] arrayChange(int[] nums, int[][] operations) {
        int[] numToIndexArr = new int[1000001];
        for (int i = 0; i < nums.length; i++) {
            numToIndexArr[nums[i]] = i;
        }

        for (int[] operation : operations) {
            int index = numToIndexArr[operation[0]];
            nums[index] = operation[1];
            numToIndexArr[operation[1]] = index;
        }

        return nums;
    }
}
```
- Runtime: 12 ms (Beats: 99.76%)
- Memory: 82.48 MB (Beats: 96.63%)

<br>
