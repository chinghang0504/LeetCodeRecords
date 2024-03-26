# [LeetCode Records](../README.md) - Question 15 3Sum

### Attempt 1: Use a Set and a HashMap
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Set<List<Integer>> result = new HashSet<>();
        
        for (int i = 0; i < nums.length - 2; i++) {
            if (i >= 1 && nums[i] == nums[i - 1]) {
                continue;
            }
            twoSum(nums, - nums[i], i, result);
        }

        return result.stream().toList();
    }

    void twoSum(int[] nums, int target, int selectedIndex, Set<List<Integer>> result) {
        HashMap<Integer, Integer> hashMap = new HashMap<Integer, Integer>();
        for (int i = selectedIndex + 1; i < nums.length; i++) {
            int nextNum = target - nums[i];
            Integer nextNumIndex = hashMap.get(nextNum);

            if (nextNumIndex != null) {
                result.add(Arrays.asList(nums[selectedIndex], nums[i], nums[nextNumIndex]).stream().sorted().toList());
            } else {
                hashMap.put(nums[i], i);
            }
        }
    }
}
```
- Runtime: 559 ms (Beats: 20.28%)
- Memory: 52.96 MB (Beats: 12.23%)

<br>

### Attempt 2: Remove a checking in the loop
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Set<List<Integer>> result = new HashSet<>();
        
        twoSum(nums, - nums[0], 0, result);
        for (int i = 1; i < nums.length - 2; i++) {
            if (nums[i] == nums[i - 1]) {
                continue;
            }
            twoSum(nums, - nums[i], i, result);
        }

        return result.stream().toList();
    }

    void twoSum(int[] nums, int target, int selectedIndex, Set<List<Integer>> result) {
        HashMap<Integer, Integer> hashMap = new HashMap<Integer, Integer>();
        for (int i = selectedIndex + 1; i < nums.length; i++) {
            int nextNum = target - nums[i];
            Integer nextNumIndex = hashMap.get(nextNum);

            if (nextNumIndex != null) {
                result.add(Arrays.asList(nums[selectedIndex], nums[i], nums[nextNumIndex]).stream().sorted().toList());
            } else {
                hashMap.put(nums[i], i);
            }
        }
    }
}
```
- Runtime: 541 ms (Beats: 21.95%)
- Memory: 52.92 MB (Beats: 12.23%)

<br>

### Attempt 3: Sort the array first
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        
        Set<List<Integer>> result = new HashSet<>();

        twoSum(nums, -nums[0], 0, result);
        for (int i = 1; i < nums.length - 2; i++) {
            if (nums[i] == nums[i - 1]) {
                continue;
            }
            twoSum(nums, -nums[i], i, result);
        }

        return result.stream().toList();
    }

    void twoSum(int[] nums, int target, int selectedIndex, Set<List<Integer>> result) {
        HashMap<Integer, Integer> hashMap = new HashMap<Integer, Integer>();
        for (int i = selectedIndex + 1; i < nums.length; i++) {
            int nextNum = target - nums[i];
            Integer nextNumIndex = hashMap.get(nextNum);

            if (nextNumIndex != null) {
                result.add(Arrays.asList(nums[selectedIndex], nums[i], nums[nextNumIndex]));
            } else {
                hashMap.put(nums[i], i);
            }
        }
    }
}
```
- Runtime: 405 ms (Beats: 28.09%)
- Memory: 52.85 MB (Beats: 13.45%)

<br>
