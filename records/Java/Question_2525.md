# [LeetCode Records](../../README.md) - Question 2525 Categorize Box According to Criteria

### Attempt 1: Use type casting
```java
class Solution {
    public String categorizeBox(int length, int width, int height, int mass) {
        boolean isBulky = getIsBulky(length, width, height);
        boolean isHeavy = getIsHeavy(mass);

        if (isBulky && isHeavy) {
            return "Both";
        } else if (isBulky) {
            return "Bulky";
        } else if (isHeavy) {
            return "Heavy";
        } else {
            return "Neither";
        }
    }

    private boolean getIsBulky(int length, int width, int height) {
        if (length >= 10_000 || width >= 10_000 || height >= 10_000) {
            return true;
        }

        long volume = (long)length * (long)width * (long)height;
        return volume >= 1000_000_000;
    }

    private boolean getIsHeavy(int mass) {
        return mass >= 100;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.38 MB (Beats: 91.54%)

<br>
