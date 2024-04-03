# [LeetCode Records](../README.md) - Question 228 Summary Ranges

### Attempt 1: Record the start and end of range
```java
class Solution {
    public List<String> summaryRanges(int[] nums) {
        List<String> result = new ArrayList<>();

        if (nums.length == 0) {
            return result;
        }

        int a = nums[0];
        int b = a;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != b + 1) {
                if (a == b) {
                    result.add("" + a);
                } else {
                    result.add("" + a + "->" + b);
                }

                a = nums[i];
            }

            b = nums[i];
        }
        if (a == b) {
            result.add("" + a);
        } else {
            result.add("" + a + "->" + b);
        }

        return result;
    }
}
```
- Runtime: 5 ms (Beats: 79.88%)
- Memory: 41.74 MB (Beats: 29.78%)

<br>

### Attempt 2: Use String.format
```java
class Solution {
    public List<String> summaryRanges(int[] nums) {
        List<String> result = new ArrayList<>();

        if (nums.length == 0) {
            return result;
        }

        int a = nums[0];
        int b = a;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != b + 1) {
                if (a == b) {
                    result.add(String.format("%d", a));
                } else {
                    result.add(String.format("%d->%d", a, b));
                }

                a = nums[i];
            }

            b = nums[i];
        }
        if (a == b) {
            result.add(String.format("%d", a));
        } else {
            result.add(String.format("%d->%d", a, b));
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 87.69%)
- Memory: 40.99 MB (Beats: 98.94%)

<br>
