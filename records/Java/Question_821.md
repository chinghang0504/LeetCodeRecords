# [LeetCode Records](../../README.md) - Question 821 Shortest Distance to a Character

### Attempt 1: Create an int[] that records the index of target character
```java
class Solution {
    
    private final static int[] records = new int[10000];
    private int count;

    public int[] shortestToChar(String s, char c) {
        count = 0;

        char[] arr = s.toCharArray();
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == c) {
                records[count] = i;
                count++;
            }
        }
        records[count] = Integer.MAX_VALUE;
        count++;

        int[] result = new int[arr.length];
        int index1 = records[0];
        int index2 = records[1];
        int curr = 2;

        for (int i = 0; i < arr.length; i++) {
            int diff1 = Math.abs(i - index1);
            int diff2 = Math.abs(index2 - i);

            if (diff1 <= diff2) {
                result[i] = diff1;
            } else {
                result[i] = diff2;
                index1 = index2;
                index2 = records[curr];
                curr++;
            }
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 98.40%)
- Memory: 42.46 MB (Beats: 48.10%)

<br>
