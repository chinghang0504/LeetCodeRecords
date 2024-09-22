# [LeetCode Records](../../README.md) - Question 1387 Sort Integers by The Power Value

### Attempt 1: Use a HashMap to store the key and its power
```java
class Solution {
    public int getKth(int lo, int hi, int k) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = lo; i <= hi; i++) {
            map.put(i, getPower(i));
        }

        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(map.entrySet());
        list.sort((e1, e2) -> {
            int e1Val = e1.getValue();
            int e2Val = e2.getValue();
            if (e1Val < e2Val) {
                return -1;
            } else if (e1Val > e2Val) {
                return 1;
            }

            int e1Key = e1.getKey();
            int e2Key = e2.getKey();
            return e1Key - e2Key;
        });

        return list.get(k - 1).getKey();
    }

    private int getPower(int num) {
        int power = 0;

        while (num != 1) {
            if (num % 2 == 1) {
                num = 3 * num + 1;
            } else {
                num /= 2;
            }

            power++;
        }

        return power;
    }
}
```
- Runtime: 48 ms (Beats: 39.83%)
- Memory: 43.85 MB (Beats: 77.99%)

<br>
