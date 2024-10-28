# [LeetCode Records](../../README.md) - Question 380 Insert Delete GetRandom O(1)

### Attempt 1: Use a HashSet to store the numbers
```java
class RandomizedSet {

    private Set<Integer> set;
    private Random random;

    public RandomizedSet() {
        set = new HashSet<>();
        random = new Random();
    }
    
    public boolean insert(int val) {
        return set.add(val);
    }
    
    public boolean remove(int val) {
        return set.remove(val);
    }
    
    public int getRandom() {
        Integer[] nums = set.toArray(Integer[]::new);
        int index = random.nextInt(nums.length);
        return nums[index];
    }
}

/**
 * Your RandomizedSet object will be instantiated and called as such:
 * RandomizedSet obj = new RandomizedSet();
 * boolean param_1 = obj.insert(val);
 * boolean param_2 = obj.remove(val);
 * int param_3 = obj.getRandom();
 */
```
- Runtime: 127 ms (Beats: 11.23%)
- Memory: 88.86 MB (Beats: 72.71%)

<br>
