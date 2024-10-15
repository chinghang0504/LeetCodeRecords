# [LeetCode Records](../../README.md) - Question 1101 The Earliest Moment When Everyone Become Friends

### Attempt 1: Use an ArrayList to store the people relationships
```java
class Solution {
    public int earliestAcq(int[][] logs, int n) {
        List<Set<Integer>> list = new ArrayList<>();
        boolean[] checked = new boolean[n];

        Arrays.sort(logs, (l1, l2) -> l1[0] - l2[0]);

        for (int[] log : logs) {
            if (!checked[log[1]] && !checked[log[2]]) {
                Set<Integer> set = new HashSet<>();
                set.add(log[1]);
                set.add(log[2]);
                list.add(set);
                checked[log[1]] = true;
                checked[log[2]] = true;
            } else if (!checked[log[1]]) {
                for (Set<Integer> set : list) {
                    if (set.contains(log[2])) {
                        set.add(log[1]);
                        checked[log[1]] = true;
                        break;
                    }
                }
            } else if (!checked[log[2]]) {
                for (Set<Integer> set : list) {
                    if (set.contains(log[1])) {
                        set.add(log[2]);
                        checked[log[2]] = true;
                        break;
                    }
                }
            } else {
                Set<Integer> set1 = null;
                Set<Integer> set2 = null;
                for (Set<Integer> set : list) {
                    if (set.contains(log[1])) {
                        set1 = set;
                    }
                    if (set.contains(log[2])) {
                        set2 = set;
                    }

                    if (set1 != null && set2 != null) {
                        break;
                    }
                }

                if (set1 != set2) {
                    set1.addAll(set2);
                    list.remove(set2);
                }
            }

            if (list.size() == 1 && list.get(0).size() == n) {
                return log[0];
            }
        }

        return -1;
    }
}
```
- Runtime: 8 ms (Beats: 18.20%)
- Memory: 44.33 MB (Beats: 65.72%)

<br>
