# [LeetCode Records](../../README.md) - Question 1742 Maximum Number of Balls in a Box

### Attempt 1: Use a HashMap to save the counts
```java
class Solution {
    public int countBalls(int lowLimit, int highLimit) {
        Map<Integer, Integer> map = new HashMap<>();
        int max = 1;

        for (int i = lowLimit; i <= highLimit; i++) {
            int boxNum = getBoxNum(i);
            Integer boxCount = map.get(boxNum);
            if (boxCount == null) {
                map.put(boxNum, 1);
            } else {
                int nextCount = boxCount + 1;
                max = Math.max(max, nextCount);
                map.put(boxNum, nextCount);
            }
        }

        return max;
    }

    private int getBoxNum(int num) {
        int sum = 0;

        while (num > 0) {
            sum += num % 10;
            num /= 10;
        }

        return sum;
    }
}
```
- Runtime: 30 ms (Beats: 38.23%)
- Memory: 44.23 MB (Beats: 36.22%)

<br>

### Attempt 2: Use a int[] to save the counts
```java
class Solution {
    public int countBalls(int lowLimit, int highLimit) {
        int[] boxCounts = new int[46];
        int max = 0;

        for (int i = lowLimit; i <= highLimit; i++) {
            int boxNum = getBoxNum(i);
            boxCounts[boxNum]++;
            max = Math.max(max, boxCounts[boxNum]);
        }

        return max;
    }

    private int getBoxNum(int num) {
        int sum = 0;

        while (num > 0) {
            sum += num % 10;
            num /= 10;
        }

        return sum;
    }
}
```
- Runtime: 15 ms (Beats: 67.00%)
- Memory: 40.52 MB (Beats: 68.01%)

<br>
