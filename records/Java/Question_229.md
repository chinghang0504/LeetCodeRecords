# [LeetCode Records](../../README.md) - Question 229 Majority Element II

### Attempt 1: Use a HashMap
```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            Integer count = hashMap.get(nums[i]);
            if (count == null) {
                hashMap.put(nums[i], 1);
            } else {
                hashMap.put(nums[i], count + 1);
            }
        }

        int count = nums.length / 3;
        List<Integer> result = new ArrayList<>();
        for (int key : hashMap.keySet()) {
            if (hashMap.get(key) > count) {
                result.add(key);
            }
        }

        return result;
    }
}
```
- Runtime: 9 ms (Beats: 47.53%)
- Memory: 47.05 MB (Beats: 96.52%)

<br>

### Attempt 2: Use merge()
```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            hashMap.merge(nums[i], 1, Integer::sum);
        }

        int count = nums.length / 3;
        List<Integer> result = new ArrayList<>();
        for (int key : hashMap.keySet()) {
            if (hashMap.get(key) > count) {
                result.add(key);
            }
        }

        return result;
    }
}
```
- Runtime: 8 ms (Beats: 47.96%)
- Memory: 47.69 MB (Beats: 63.50%)

<br>
