# [LeetCode Records](../README.md) - Question 136 Single Number

### Attempt 1: Use a HashMap
```java
class Solution {
    public int singleNumber(int[] nums) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            Integer curr = hashMap.get(nums[i]);
            if (curr == null) {
                hashMap.put(nums[i], 1);
            } else {
                hashMap.remove(nums[i]);
            }
        }

        return hashMap.keySet().iterator().next();
    }
}
```
- Runtime: 14 ms (Beats: 15.51%)
- Memory: 44.84 MB (Beats: 91.92%)

<br>

### Attempt 2: Use xor operator
```java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;

        for (int i = 0; i < nums.length; i++) {
            result ^= nums[i];
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 99.85%)
- Memory: 46.02 MB (Beats: 44.90%)

<br>
