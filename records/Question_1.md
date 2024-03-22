# [LeetCode Records](../README.md) - Question 1 Two Sum

### Attemp 1: Use two loops
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int length = nums.length;

        for (int i = 0; i < length-1; i++) {
            for (int j = i+1; j < length; j++) {
                if (nums[i] + nums[j] == target) {
                    int[] answer = { i, j };
                    return answer;
                }
            }
        }

        return null;
    }
}
```
- Runtime: 38 ms (Beats: 47.67%)
- Memory: 45.16 MB (Beats: 9.84%)

<br>

### Attemp 2: Reduce one calculation in the inner loop
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int length = nums.length;

        for (int i = 0; i < length-1; i++) {
            int nextNum = target - nums[i];
            
            for (int j = i+1; j < length; j++) {
                if (nums[j] == nextNum) {
                    int[] answer = { i, j };
                    return answer;
                }
            }
        }

        return null;
    }
}
```
- Runtime: 32 ms (Beats: 52.89%)
- Memory: 44.54 MB (Beats: 84.34%)

<br>

### Attemp 3: Use HashMap
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> hashMap = new HashMap<Integer, Integer>();
        for (int i = 0; i < nums.length; i++) {
            hashMap.put(nums[i], i);
        }

        for (int i = 0; i < nums.length; i++) {
            int nextNum = target - nums[i];
            Integer nextNumIndex = hashMap.get(nextNum);

            if (nextNumIndex != null && i != nextNumIndex) {
                int[] answer = { i, nextNumIndex };
                return answer;
            }
        }

        return null;
    }
}
```
- Runtime: 4 ms (Beats: 64.50%)
- Memory: 44.95 MB (Beats: 29.47%)

<br>

### Attemp 4: Check when pushing elements to HashMap
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> hashMap = new HashMap<Integer, Integer>();
        for (int i = 0; i < nums.length; i++) {
            int nextNum = target - nums[i];
            Integer nextNumIndex = hashMap.get(nextNum);

            if (nextNumIndex != null) {
                return new int[] { i, nextNumIndex };
            } else {
                hashMap.put(nums[i], i);
            }
        }

        return null;
    }
}
```
- Runtime: 2 ms (Beats: 97.88%)
- Memory: 44.94 MB (Beats: 29.47%)

<br>
