# [LeetCode Records](../../README.md) - Question 1093 Statistics from a Large Sample

### Attempt 1: Record the minimum number and the maximum number first
```java
class Solution {
    public double[] sampleStats(int[] count) {
        int minNum = 0;
        while (count[minNum] == 0) {
            minNum++;
        }

        int maxNum = count.length - 1;
        while (count[maxNum] == 0) {
            maxNum--;
        }

        long sum = 0;
        long size = 0;
        int maxCount = 0;
        int maxCountNum = 0;
        for (int i = minNum; i <= maxNum; i++) {
            sum += (long)(count[i]) * i;
            size += count[i];

            if (count[i] > maxCount) {
                maxCount = count[i];
                maxCountNum = i;
            }
        }

        double median = 0.0;
        long targetCount = size / 2;
        if (size % 2 == 1) {
            targetCount++;
            long currCount = 0;
            int i = minNum;
            while (true) {
                currCount += count[i];
                if (currCount >= targetCount) {
                    median = i;
                    break;
                }
                i++;
            }
        } else {
            long currCount = 0;
            int i = minNum;
            while (true) {
                currCount += count[i];
                if (currCount > targetCount) {
                    median = i;
                    break;
                } else if (currCount == targetCount) {
                    median = i;
                    i++;
                    while (count[i] == 0) {
                        i++;
                    }
                    median = (median + i) / 2;
                    break;
                }
                i++;
            }
        }

        return new double[] { minNum, maxNum, (double)sum / size, median, maxCountNum };
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.40 MB (Beats: 65.00%)

<br>
