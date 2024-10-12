# [LeetCode Records](../../README.md) - Question 539 Minimum Time Difference

### Attempt 1: Use an ArrayList to store the time values and Arrays.sort() to sort the ArrayList
```java
class Solution {
    public int findMinDifference(List<String> timePoints) {
        List<Integer> list = new ArrayList<>();
        for (String time : timePoints) {
            list.add(getTimeValue(time));
        }
        list.sort(null);

        int prevTime = list.get(0);
        int minTimeDiff = Integer.MAX_VALUE;
        int size = list.size();
        for (int i = 1; i < size; i++) {
            int currTime = list.get(i);
            minTimeDiff = Math.min(minTimeDiff, currTime - prevTime);
            prevTime = currTime;
        }
        minTimeDiff = Math.min(minTimeDiff, 1440 - list.getLast() + list.getFirst());

        return minTimeDiff;
    }

    private int getTimeValue(String time) {
        char[] arr = time.toCharArray();
        int hour = (arr[0] - '0') * 10 + arr[1] - '0';
        int minute = (arr[3] - '0') * 10 + arr[4] - '0';
        return hour * 60 + minute;
    }
}
```
- Runtime: 8 ms (Beats: 44.52%)
- Memory: 45.02 MB (Beats: 84.20%)

<br>
