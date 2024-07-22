# [LeetCode Records](../../README.md) - Question 2859 Sum of Values at Indices With K Set Bits

### Attempt 1: Ue a helper function to check the set bits
```java
class Solution {
    public int sumIndicesWithKSetBits(List<Integer> nums, int k) {
        int sum = 0;

        int i = 0;
        for (int num : nums) {
            if (isTarget(i, k)) {
                sum += num;
            }

            i++;
        }

        return sum;
    }

    private boolean isTarget(int num, int k) {
        int count = 0;

        while (num > 0) {
            count += num & 1;
            num >>>= 1;
        }

        return count == k;
    }
}
```
- Runtime: 2 ms (Beats: 38.46%)
- Memory: 44.10 MB (Beats: 74.48%)

<br>
