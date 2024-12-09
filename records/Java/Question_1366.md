# [LeetCode Records](../../README.md) - Question 1366 Rank Teams by Votes

### Attempt 1: Use a HashMap to store the character and its counts key-value pairs
```java
class Solution {
    public String rankTeams(String[] votes) {
        int size = votes[0].length();
        Map<Character, int[]> map = new HashMap<>();

        for (String vote : votes) {
            char[] arr = vote.toCharArray();

            for (int i = 0; i < arr.length; i++) {
                int[] counts = map.get(arr[i]);
                if (counts == null) {
                    counts = new int[size];
                    map.put(arr[i], counts);
                }

                counts[i]++;
            }
        }

        List<Map.Entry<Character, int[]>> list = new ArrayList<>(map.entrySet());
        list.sort((e1, e2) -> {
            int[] counts1 = e1.getValue();
            int[] counts2 = e2.getValue();
            for (int i = 0; i < size; i++) {
                if (counts1[i] != counts2[i]) {
                    return counts2[i] - counts1[i];
                }
            }

            return 0;
        });

        StringBuilder stringBuilder = new StringBuilder();
        for (Map.Entry<Character, int[]> item : list) {
            stringBuilder.append(item.getKey());
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 8 ms (Beats: 63.55%)
- Memory: 44.22 MB (Beats: 53.58%)

<br>
