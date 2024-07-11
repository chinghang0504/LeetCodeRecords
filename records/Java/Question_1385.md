# [LeetCode Records](../../README.md) - Question 1385 Find the Distance Value Between Two Arrays

### Attempt 1: Use a loop
```java
class Solution {
    public int findTheDistanceValue(int[] arr1, int[] arr2, int d) {
        int count = 0;

        for (int i = 0; i < arr1.length; i++) {
            boolean isGood = true;
            for (int j = 0; j < arr2.length; j++) {
                if (Math.abs(arr1[i] - arr2[j]) <= d) {
                    isGood = false;
                    break;
                }
            }

            if (isGood) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 51.06%)
- Memory: 44.04 MB (Beats: 43.35%)

<br>
