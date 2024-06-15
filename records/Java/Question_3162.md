# [LeetCode Records](../../README.md) - Question 3162 Find the Number of Good Pairs I

### Attempt 1: Create an array for nums2[j] * k
```java
class Solution {
    public int numberOfPairs(int[] nums1, int[] nums2, int k) {
        int[] nums2Copy = nums2.clone();

        for (int i = 0; i < nums2Copy.length; i++) {
            nums2Copy[i] *= k;
        }

        int count = 0;
        
        for (int i = 0; i < nums1.length; i++) {
            for (int j = 0; j < nums2Copy.length; j++) {
                if (nums1[i] % nums2Copy[j] == 0) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 99.94%)
- Memory: 42.73 MB (Beats: 46.66%)

<br>
