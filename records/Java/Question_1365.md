# [LeetCode Records](../../README.md) - Question 1365 How Many Numbers Are Smaller Than the Current Number

### Attempt 1: Use Arrays.sort() and a HashMap
```java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        int[] copyNums = nums.clone();
        Arrays.sort(copyNums);

        Map<Integer, Integer> map = new HashMap<>();
        map.put(copyNums[0], 0);
        int currCount = 1;
        int currNum = copyNums[0];

        for (int i = 1; i < nums.length; i++) {
            if (copyNums[i] != currNum) {
                map.put(copyNums[i], currCount);
                currNum = copyNums[i];
            }

            currCount++;
        }

        int[] result = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            result[i] = map.get(nums[i]);
        }

        return result;
    }
}
```
- Runtime: 4 ms (Beats: 85.12%)
- Memory: 44.36 MB (Beats: 42.13%)

<br>
