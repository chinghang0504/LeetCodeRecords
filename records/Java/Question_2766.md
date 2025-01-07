# [LeetCode Records](../../README.md) - Question 2766 Relocate Marbles

### Attempt 1: Use a HashSet to store the positions
```java
class Solution {
    public List<Integer> relocateMarbles(int[] nums, int[] moveFrom, int[] moveTo) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }

        for (int i = 0; i < moveFrom.length; i++) {
            if (set.contains(moveFrom[i])) {
                set.remove(moveFrom[i]);
                set.add(moveTo[i]);
            }
        }

        List<Integer> ans = new ArrayList<>(set);
        ans.sort(null);

        return ans;
    }
}
```
- Runtime: 49 ms (Beats: 82.61%)
- Memory: 60.50 MB (Beats: 82.61%)

<br>

### Attempt 2: Without using remove()
```java
class Solution {
    public List<Integer> relocateMarbles(int[] nums, int[] moveFrom, int[] moveTo) {
        List<Integer> ans = new ArrayList<>();
        Set<Integer> set = new HashSet<>();

        int n = moveFrom.length;
        for (int i = n - 1; i >= 0; i--) {
            if (!set.contains(moveTo[i])) {
                set.add(moveTo[i]);
                ans.add(moveTo[i]);
            }
            set.add(moveFrom[i]);
        }

        for (int num : nums) {
            if (!set.contains(num)) {
                set.add(num);
                ans.add(num);
            }
        }

        ans.sort(null);

        return ans;
    }
}
```
- Runtime: 46 ms (Beats: 100.00%)
- Memory: 62.33 MB (Beats: 57.61%)

<br>
