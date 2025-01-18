# [LeetCode Records](../../README.md) - Question 2554 Maximum Number of Integers to Choose From a Range I

### Attempt 1: Use a HashSet to store the banned numbers
```java
class Solution {
    public int maxCount(int[] banned, int n, int maxSum) {
        Set<Integer> bannedSet = new HashSet<>();
        for (int bannedNum : banned) {
            bannedSet.add(bannedNum);
        }

        int count = 0;
        int sum = 0;
        for (int i = 1; i <= n; i++) {
            if (bannedSet.contains(i)) {
                continue;
            }

            int nextSum = sum + i;
            if (nextSum <= maxSum) {
                sum = nextSum;
                count++;
            } else {
                break;
            }
        }

        return count;
    }
}
```
- Runtime: 47 ms (Beats: 54.71%)
- Memory: 45.60 MB (Beats: 89.60%)

<br>

### Attempt 2: Use an boolean array to store the banned numbers
```java
class Solution {
    public int maxCount(int[] banned, int n, int maxSum) {
        boolean[] bannedNumArr = new boolean[10001];
        for (int bannedNum : banned) {
            bannedNumArr[bannedNum] = true;
        }

        int count = 0;
        int sum = 0;
        for (int i = 1; i <= n; i++) {
            if (bannedNumArr[i]) {
                continue;
            }

            int nextSum = sum + i;
            if (nextSum <= maxSum) {
                sum = nextSum;
                count++;
            } else {
                break;
            }
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 99.99%)
- Memory: 46.02 MB (Beats: 42.45%)

<br>
