# [LeetCode Records](../../README.md) - Question 2838 Maximum Coins Heroes Can Collect

### Attempt 1: Use a HashMap to store the monster and coin key-value pairs
```java
class Solution {
    public long[] maximumCoins(int[] heroes, int[] monsters, int[] coins) {
        Map<Integer, Long> map = new HashMap<>();
        for (int i = 0; i < monsters.length; i++) {
            map.merge(monsters[i], (long)coins[i], Long::sum);
        }

        List<Map.Entry<Integer, Long>> list = new ArrayList<>(map.entrySet());
        list.sort(Map.Entry.comparingByKey());
        long currSum = 0;
        for (Map.Entry<Integer, Long> entry : list) {
            currSum += entry.getValue();
            entry.setValue(currSum);
        }

        int size = list.size();
        long[] ans = new long[heroes.length];
        for (int i = 0; i < heroes.length; i++) {
            Map.Entry<Integer, Long> firstEntry = list.get(0);
            if (heroes[i] < firstEntry.getKey()) {
                continue;
            }

            int lower = 0;
            int upper = size - 1;
            while (true) {
                int middle = (lower + upper) / 2;
                Map.Entry<Integer, Long> entry = list.get(middle);
                int power = entry.getKey();

                if (heroes[i] == power) {
                    ans[i] = entry.getValue();
                    break;
                } else if (heroes[i] < power) {
                    upper = middle - 1;
                } else {
                    lower = middle;
                }

                if (lower == upper) {
                    ans[i] = list.get(lower).getValue();
                    break;
                } else if (lower + 1 == upper) {
                    entry = list.get(upper);
                    ans[i] = heroes[i] >= entry.getKey() ? entry.getValue() : list.get(lower).getValue();
                    break;
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 126 ms (Beats: 12.12%)
- Memory: 61.10 MB (Beats: 18.18%)

<br>
