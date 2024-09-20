# [LeetCode Records](../../README.md) - Question 3016 Minimum Number of Pushes to Type Word II

### Attempt 1: Use a HashMap to store the character and character count key-value pairs
```java
class Solution {
    public int minimumPushes(String word) {
        Map<Character, Integer> map = new HashMap<>();

        for (char ch : word.toCharArray()) {
            map.merge(ch, 1, Integer::sum);
        }

        int totalNumOfPushes = 0;
        List<Map.Entry<Character, Integer>> list = new ArrayList<>(map.entrySet());
        list.sort((e1 , e2) -> e2.getValue() - e1.getValue());

        int currNumOfPushes = 1;
        int localCount = 0;
        for (Map.Entry<Character, Integer> entry : list) {
            if (localCount == 8) {
                localCount = 0;
                currNumOfPushes++;
            }

            totalNumOfPushes += currNumOfPushes * entry.getValue();
            localCount++;
        }

        return totalNumOfPushes;
    }
}
```
- Runtime: 61 ms (Beats: 26.73%)
- Memory: 45.78 MB (Beats: 36.14%)

<br>
