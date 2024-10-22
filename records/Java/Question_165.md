# [LeetCode Records](../../README.md) - Question 165 Compare Version Numbers

### Attempt 1: Use split() to separate the numbers
```java
class Solution {
    public int compareVersion(String version1, String version2) {
        String[] splits1 = version1.split("\\.");
        String[] splits2 = version2.split("\\.");

        int size1 = splits1.length;
        int size2 = splits2.length;
        int minSize = Math.min(size1, size2);
        int i = 0;
        while (i < minSize) {
            int val1 = Integer.valueOf(splits1[i]);
            int val2 = Integer.valueOf(splits2[i]);
            if (val1 < val2) {
                return -1;
            } else if (val1 > val2) {
                return 1;
            }
            i++;
        }

        if (size1 == size2) {
            return 0;
        }

        while (i < size1) {
            int val = Integer.valueOf(splits1[i]);
            if (val > 0) {
                return 1;
            }
            i++;
        }
        while (i < size2) {
            int val = Integer.valueOf(splits2[i]);
            if (val > 0) {
                return -1;
            }
            i++;
        }

        return 0;
    }
}
```
- Runtime: 1 ms (Beats: 75.27%)
- Memory: 41.44 MB (Beats: 51.24%)

<br>
