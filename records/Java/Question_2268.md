# [LeetCode Records](../../README.md) - Question 2268 Minimum Number of Keypresses

### Attempt 1: Use a HashMap to store the character counts
```java
class Solution {
    public int minimumKeypresses(String s) {
        Map<Character, Integer> map = new HashMap<>();

        for (char ch : s.toCharArray()) {
            map.merge(ch, 1, Integer::sum);
        }

        List<Map.Entry<Character, Integer>> list = new ArrayList<>(map.entrySet());
        list.sort((e1, e2) -> e2.getValue() - e1.getValue());

        int count = 0;
        int currNumOfClick = 1;
        int round = 0;
        for (Map.Entry<Character, Integer> entry : list) {
            if (round == 9) {
                round = 0;
                currNumOfClick++;
            }

            count += entry.getValue() * currNumOfClick;
            round++;
        }

        return count;
    }
}
```
- Runtime: 18 ms (Beats: 28.81%)
- Memory: 45.53 MB (Beats: 19.11%)

<br>
