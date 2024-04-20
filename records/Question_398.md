# [LeetCode Records](../README.md) - Question 398 Random Pick Index

### Attempt 1: Use a HashMap to save the index
```java
class Solution {

    private Random random;
    private Map<Integer, List<Integer>> map;

    public Solution(int[] nums) {
        random = new Random();
        map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            List<Integer> value = map.get(nums[i]);
            if (value != null) {
                value.add(i);
            } else {
                value = new ArrayList<>();
                value.add(i);
                map.put(nums[i], value);
            }
        }
    }
    
    public int pick(int target) {
        List<Integer> value = map.get(target);
        int index = random.nextInt(value.size());
        return value.get(index);
    }
}
```
- Runtime: 80 ms (Beats: 66.20%)
- Memory: 55.25 MB (Beats: 86.26%)

<br>

### Attempt 2: 
```java
class Solution {

    private Random random;
    private int[] nums;

    public Solution(int[] nums) {
        random = new Random();
        this.nums = nums;
    }
    
    public int pick(int target) {
        while (true) {
            int index = random.nextInt(nums.length);
            if (nums[index] == target) {
                return index;
            }
        }
    }
}
```
- Runtime: 58 ms (Beats: 98.88%)
- Memory: 55.25 MB (Beats: 86.26%)

<br>
