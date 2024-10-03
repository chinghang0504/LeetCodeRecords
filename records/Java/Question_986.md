# [LeetCode Records](../../README.md) - Question 986 Interval List Intersections

### Attempt 1: Use an int[][] to store the time intervals
```java
class Solution {
    public int[][] intervalIntersection(int[][] firstList, int[][] secondList) {
        int[][] ans = new int[1000][2];
        int size = 0;

        int leftIndex = 0;
        int rightIndex = 0;
        while (leftIndex < firstList.length && rightIndex < secondList.length) {
            int start = Math.max(firstList[leftIndex][0], secondList[rightIndex][0]);
            int end = Math.min(firstList[leftIndex][1], secondList[rightIndex][1]);
            if (start <= end) {
                ans[size][0] = start;
                ans[size][1] = end;
                size++;
            }
            
            if (firstList[leftIndex][1] < secondList[rightIndex][1]) {
                leftIndex++;
            } else if (firstList[leftIndex][1] > secondList[rightIndex][1]) {
                rightIndex++;
            } else {
                leftIndex++;
                rightIndex++;
            }
        }

        return Arrays.copyOf(ans, size);
    }
}
```
- Runtime: 6 ms (Beats: 11.30%)
- Memory: 45.40 MB (Beats: 81.15%)

<br>

### Attempt 2: Use an ArrayList to store the time intervals
```java
class Solution {
    public int[][] intervalIntersection(int[][] firstList, int[][] secondList) {
        List<int[]> list = new ArrayList<>();

        int leftIndex = 0;
        int rightIndex = 0;
        while (leftIndex < firstList.length && rightIndex < secondList.length) {
            int start = Math.max(firstList[leftIndex][0], secondList[rightIndex][0]);
            int end = Math.min(firstList[leftIndex][1], secondList[rightIndex][1]);
            if (start <= end) {
                list.add(new int[]{ start, end });
            }
            
            if (firstList[leftIndex][1] < secondList[rightIndex][1]) {
                leftIndex++;
            } else if (firstList[leftIndex][1] > secondList[rightIndex][1]) {
                rightIndex++;
            } else {
                leftIndex++;
                rightIndex++;
            }
        }

        return list.toArray(int[][]::new);
    }
}
```
- Runtime: 4 ms (Beats: 60.38%)
- Memory: 45.44 MB (Beats: 68.07%)

<br>
