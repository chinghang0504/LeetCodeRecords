# [LeetCode Records](../../README.md) - Question 55 Jump Game

### Attempt 1: Use a HashSet to record which index is already added
```java
class Solution {
    public boolean canJump(int[] nums) {
        int target = nums.length - 1;
        HashSet<Integer> added = new HashSet<>();
        HashSet<Integer> prevSaved = new HashSet<>();
        added.add(0);
        prevSaved.add(0);

        while (!prevSaved.isEmpty()) {
            HashSet<Integer> saved = new HashSet<>();
            Iterator<Integer> iterator = prevSaved.iterator();

            while (iterator.hasNext()) {
                int index = iterator.next();

                int nextIndex = index + 1;
                int endIndex = nextIndex + nums[index] - 1;
                if (endIndex >= nums.length - 1) {
                    return true;
                }

                for (; nextIndex <= endIndex; nextIndex++) {
                    if (added.add(nextIndex)) {
                        saved.add(nextIndex);
                    }
                }
            }

            prevSaved = saved;
        }

        return false;
    }
}
```
- Runtime: 753 ms (Beats: 5.01%)
- Memory: 46.25 MB (Beats: 5.29%)

<br>
