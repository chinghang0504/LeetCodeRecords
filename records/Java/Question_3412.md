# [LeetCode Records](../../README.md) - Question 3412 Find Mirror Score of a String

### Attempt 1: Use a HashMap to store the character and its index list key-value pairs
```java
class Solution {
    public long calculateScore(String s) {
        Map<Character, List<Integer>> charToIndexListMap = new HashMap<>();
        for (char ch = 'a'; ch <= 'z'; ch++) {
            charToIndexListMap.put(ch, new ArrayList<>());
        }

        char[] arr = s.toCharArray();
        long score = 0;
        for (int i = 0; i < arr.length; i++) {
            char targetCh = (char)(25 - (arr[i] - 'a') + 'a');
            List<Integer> targetList = charToIndexListMap.get(targetCh);
            if (!targetList.isEmpty()) {
                score += i - targetList.removeLast();
            } else {
                charToIndexListMap.get(arr[i]).add(i);
            }
        }

        return score;
    }
}
```
- Runtime: 23 ms (Beats: 88.36%)
- Memory: 45.54 MB (Beats: 85.29%)

<br>
