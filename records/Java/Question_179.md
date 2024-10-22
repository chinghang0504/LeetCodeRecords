# [LeetCode Records](../../README.md) - Question 179 Largest Number

### Attempt 1: Use Arrays.sort() to sort the number
```java
class Solution {
    public String largestNumber(int[] nums) {
        String[] numStrs = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            numStrs[i] = String.valueOf(nums[i]);
        }

        Arrays.sort(numStrs, (numStr1, numStr2) -> {
            String str1 = numStr1 + numStr2;
            String str2 = numStr2 + numStr1;
            return -1 * str1.compareTo(str2);
        });

        if (numStrs[0].equals("0")) {
            return "0";
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (String numStr : numStrs) {
            stringBuilder.append(numStr);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 5 ms (Beats: 97.06%)
- Memory: 43.46 MB (Beats: 33.51%)

<br>
