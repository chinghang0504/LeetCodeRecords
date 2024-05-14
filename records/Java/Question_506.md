# [LeetCode Records](../../README.md) - Question 506 Relative Ranks

### Attempt 1: Use a HashMap and a String[]
```java
class Solution {
    public String[] findRelativeRanks(int[] score) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < score.length; i++) {
            map.put(score[i], i);
        }

        Arrays.sort(score);

        String[] result = new String[score.length];

        if (score.length >= 3) {
            result[map.get(score[score.length - 3])] = "Bronze Medal";
            result[map.get(score[score.length - 2])] = "Silver Medal";
            result[map.get(score[score.length - 1])] = "Gold Medal";
        } else if (score.length >= 2) {
            result[map.get(score[score.length - 2])] = "Silver Medal";
            result[map.get(score[score.length - 1])] = "Gold Medal";
        } else {
            result[map.get(score[score.length - 1])] = "Gold Medal";
        }

        int curr = 4;
        for (int i = score.length - 4; i >= 0; i--, curr++) {
            result[map.get(score[i])] = String.valueOf(curr);
        }

        return result;
    }
}
```
- Runtime: 8 ms (Beats: 73.67%)
- Memory: 46.19 MB (Beats: 7.76%)

<br>
