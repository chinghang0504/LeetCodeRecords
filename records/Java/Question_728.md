# [LeetCode Records](../../README.md) - Question 728 Self Dividing Numbers

### Attempt 1: 
```java
class Solution {
    public List<Integer> selfDividingNumbers(int left, int right) {
        List<Integer> result = new ArrayList<>();

        for (int i = left; i <= right; i++) {
            int curr = i;
            while (curr > 0) {
                int remainder = curr % 10;
                if (remainder == 0 || i % remainder != 0) {
                    break;
                }
                curr /= 10;
            }

            if (curr <= 0) {
                result.add(i);
            }
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 69.86%)
- Memory: 41.31 MB (Beats: 25.28%)

<br>
