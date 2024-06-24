# [LeetCode Records](../../README.md) - Question 2553 Separate the Digits in an Array | Easy

### Attempt 1: Use an ArrayList
```java
class Solution {
    public int[] separateDigits(int[] nums) {
        List<Integer> list = new ArrayList<>();

        for (int i = nums.length - 1; i >= 0; i--) {
            int num = nums[i];
            while (num > 0) {
                list.add(num % 10);
                num /= 10;
            }
        }

        int size = list.size();
        int[] result = new int[size];
        int curr = size - 1;
        for (Integer item : list) {
            result[curr] = item;
            curr--;
        }
        
        return result;
    }
}
```
- Runtime: 4 ms (Beats: 80.54%)
- Memory: 44.54 MB (Beats: 80.35%)

<br>
