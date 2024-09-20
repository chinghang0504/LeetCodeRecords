# [LeetCode Records](../../README.md) - Question 451 Sort Characters By Frequency

### Attempt 1: Use a HashMap to store the character counts
```java
class Solution {
    public String frequencySort(String s) {
        Map<Character, Integer> map = new HashMap<>();

        for (char ch : s.toCharArray()) {
            map.merge(ch, 1, Integer::sum);
        }

        List<Map.Entry<Character, Integer>> list = new ArrayList<>(map.entrySet());
        list.sort((e1, e2) -> e2.getValue() - e1.getValue());

        StringBuilder stringBuilder = new StringBuilder();
        for (Map.Entry<Character, Integer> entry : list) {
            char ch = entry.getKey();
            int count = entry.getValue();
            for (int i = 0; i < count; i++) {
                stringBuilder.append(ch);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 10 ms (Beats: 89.71%)
- Memory: 45.44 MB (Beats: 66.56%)

<br>
