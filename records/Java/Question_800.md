# [LeetCode Records](../../README.md) - Question 800 Similar RGB Color

### Attempt 1: Test each case
```java
class Solution {
    public String similarRGB(String color) {
        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append('#');

        int i = 1;
        while (i < 7) {
            stringBuilder.append(getSimilarPart(color.substring(i, i + 2)));
            i += 2;
        }

        return stringBuilder.toString();
    }
    
    private String getSimilarPart(String part) {
        int val = Integer.valueOf(part, 16);
        
        int[] targets = { 0x00, 0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77, 0x88, 0x99, 0xAA, 0xBB, 0xCC, 0xDD, 0xEE, 0xFF };
        String[] targetStrings = { "00", "11", "22", "33", "44", "55", "66", "77", "88", "99", "aa", "bb", "cc", "dd", "ee", "ff"};
        int min = Integer.MAX_VALUE;
        int minIndex = -1;
        for (int i = 0; i < targets.length; i++) {
            int currMin = Math.abs(val - targets[i]);
            if (currMin < min) {
                min = currMin;
                minIndex = i;
            }
        }

        return targetStrings[minIndex];
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.63 MB (Beats: 65.00%)

<br>
