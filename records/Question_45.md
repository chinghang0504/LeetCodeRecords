# [LeetCode Records](../README.md) - Question 45 Jump Game II

### Attempt 1: Use two HashSet
```java
class Solution {

    public int jump(int[] nums) {
        int count = 0;
        HashSet<Integer> prevHashSet = new HashSet<>();
        prevHashSet.add(0);
        HashSet<Integer> nextHashSet;

        while (true) {
            Iterator<Integer> iterator = prevHashSet.iterator();
            nextHashSet = new HashSet<>();

            while (iterator.hasNext()) {
                int curr = iterator.next();
                if (curr >= nums.length) {
                    continue;
                } else if (curr == nums.length - 1) {
                    return count;
                }

                int step = nums[curr];
                for (int i = 0; i < step; i++) {
                    nextHashSet.add(curr + i + 1);
                }
            }

            prevHashSet = nextHashSet;
            count++;
        }
    }
}
```
- Runtime: 2568 ms (Beats: 5.09%)
- Memory: 54.85 MB (Beats: 5.20%)

<br>

### Attempt 2: Check the index before adding to HashSet
```java
class Solution {

    public int jump(int[] nums) {
        if (nums.length == 1) {
            return 0;
        }

        int count = 0;
        HashSet<Integer> prevHashSet = new HashSet<>();
        prevHashSet.add(0);
        HashSet<Integer> nextHashSet;

        while (true) {
            Iterator<Integer> iterator = prevHashSet.iterator();
            nextHashSet = new HashSet<>();

            while (iterator.hasNext()) {
                int curr = iterator.next();
                int step = nums[curr];
                for (int i = 0; i < step; i++) {
                    int next = curr + i + 1;
                    if (next >= nums.length) {
                        break;
                    } else if (next == nums.length - 1) {
                        return count + 1;
                    } else {
                        nextHashSet.add(next);
                    }
                }
            }

            prevHashSet = nextHashSet;
            count++;
        }
    }
}
```
- Runtime: 2125 ms (Beats: 5.09%)
- Memory: 54.68 MB (Beats: 5.20%)

<br>
