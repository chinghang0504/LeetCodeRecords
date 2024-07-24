# [LeetCode Records](../../README.md) - Question 2367 Number of Arithmetic Triplets

### Attempt 1: Use a nested loop
```java
class Solution {
    public int arithmeticTriplets(int[] nums, int diff) {
        int count = 0;

        for (int i = 0; i < nums.length - 2; i++) {
            for (int j = i + 1; j < nums.length - 1; j++) {
                int diff1 = nums[j] - nums[i];
                if (diff1 < diff) {
                    continue;
                } else if (diff1 > diff) {
                    break;
                }

                for (int k = j + 1; k < nums.length; k++) {
                    int diff2 = nums[k] - nums[j];
                    if (diff2 < diff) {
                        continue;
                    } else if (diff2 > diff) {
                        break;
                    } else {
                        count++;
                    }
                }
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 82.44%)
- Memory: 41.44 MB (Beats: 43.19%)

<br>
