# [LeetCode Records](../../README.md) - Question 1429 First Unique Number

### Attempt 1: Use a HashSet to store the numbers and a HashSet to store the non-unique numbers
```java
class FirstUnique {

    private Set<Integer> numSet;
    private Set<Integer> nonUniqueSet;
    private List<Integer> list;

    public FirstUnique(int[] nums) {
        numSet = new HashSet<>();
        nonUniqueSet = new HashSet<>();
        list = new LinkedList<>();

        for (int num : nums) {
            if (numSet.contains(num)) {
                nonUniqueSet.add(num);
            } else {
                numSet.add(num);
                list.add(num);
            }
        }
    }
    
    public int showFirstUnique() {
        while (!list.isEmpty()) {
            int num = list.getFirst();
            if (nonUniqueSet.contains(num)) {
                list.removeFirst();
            } else {
                return num;
            }
        }

        return -1;
    }
    
    public void add(int value) {
        if (numSet.contains(value)) {
            nonUniqueSet.add(value);
        } else {
            numSet.add(value);
            list.add(value);
        }
    }
}

/**
 * Your FirstUnique object will be instantiated and called as such:
 * FirstUnique obj = new FirstUnique(nums);
 * int param_1 = obj.showFirstUnique();
 * obj.add(value);
 */
```
- Runtime: 111 ms (Beats: 71.37%)
- Memory: 84.79 MB (Beats: 54.88%)

<br>
