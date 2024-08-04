# [LeetCode Records](../../README.md) - Question 1071 Greatest Common Divisor of Strings

### Attempt 1: Use a helper function to check the string is a divisor
```java
class Solution {
    public String gcdOfStrings(String str1, String str2) {
        String divisor = str1.length() <= str2.length() ? str1 : str2;

        for (int i = divisor.length(); i >= 1; i--) {
            divisor = divisor.substring(0, i);

            if (isCommonDivisor(str1, divisor) && isCommonDivisor(str2, divisor)) {
                return divisor;
            }
        }

        return "";
    }

    private boolean isCommonDivisor(String str, String divisor) {
        int strSize = str.length();
        int divisorSize = divisor.length();

        if (strSize % divisorSize != 0) {
            return false;
        }

        for (int i = 0; i < strSize; i += divisorSize) {
            if (!str.substring(i, i + divisorSize).equals(divisor)) {
                return false;
            }    
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 17.59%)
- Memory: 45.02 MB (Beats: 5.87%)

<br>
