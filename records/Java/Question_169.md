# [LeetCode Records](../../README.md) - Question 169 Majority Element

### Attempt 1: Use a HashMap
```java
class Solution {
    public int majorityElement(int[] nums) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            Integer count = hashMap.get(nums[i]);
            if (count == null) {
                hashMap.put(nums[i], 1);
            } else {
                hashMap.put(nums[i], count + 1);
            }
        }

        int count = nums.length / 2;
        for (int i = 0; i < nums.length; i++) {
            if (hashMap.get(nums[i]) > count) {
                return nums[i];
            }
        }
        
        return -1;
    }
}
```
- Runtime: 12 ms (Beats: 34.12%)
- Memory: 49.27 MB (Beats: 76.80%)

<br>

### Attempt 2: Use recursion
```java
class Solution {
    public int majorityElement(int[] nums) {
        return majorityElementRecursion(nums, 0);
    }

    int majorityElementRecursion(int[] nums, int index) {
        int count = 0;

        for (int i = index; i < nums.length; i++) {
            count = nums[i] == nums[index] ? count + 1 : count - 1;

            if (count < 0) {
                return majorityElementRecursion(nums, i);
            }
        }

        return nums[index];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 52.78 MB (Beats: 27.65%)

<br>
