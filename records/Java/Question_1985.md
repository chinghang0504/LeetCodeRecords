# [LeetCode Records](../../README.md) - Question 1985 Find the Kth Largest Integer in the Array

### Attempt 1: Use Arrays.sort() to the array of the number strings
```java
class Solution {
    public String kthLargestNumber(String[] nums, int k) {
        Arrays.sort(nums, (n1, n2) -> {
            int len1 = n1.length();
            int len2 = n2.length();
            if (len1 != len2) {
                return len2 - len1;
            } else {
                return n2.compareTo(n1);
            }
        });

        return nums[k - 1];
    }
}
```
- Runtime: 15 ms (Beats: 98.93%)
- Memory: 49.31 MB (Beats: 99.55%)

<br>
