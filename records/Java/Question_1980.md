# [LeetCode Records](../../README.md) - Question 1980 Find Unique Binary String

### Attempt 1: Use Integer.parseInt() to convert a string to a binary integer
```java
class Solution {
    public String findDifferentBinaryString(String[] nums) {
        Set<Integer> set = new HashSet<>();

        for (String num : nums) {
            set.add(Integer.parseInt(num, 2));
        }

        int n = (int)Math.pow(2, nums.length);
        for (int i = 0; i < n; i++) {
            if (!set.contains(i)) {
                String val = Integer.toBinaryString(i);
                String format = "%" + nums.length + "s";
                return String.format(format, val).replace(" ", "0");
            }
        }

        return "";
    }
}
```
- Runtime: 10 ms (Beats: 23.96%)
- Memory: 42.32 MB (Beats: 22.78%)

<br>
