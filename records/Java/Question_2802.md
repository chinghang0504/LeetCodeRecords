# [LeetCode Records](../../README.md) - Question 2802 Find The K-th Lucky Number

### Attempt 1: Find the remainder for each iteration
```java
class Solution {
    public String kthLuckyNumber(int k) {
        List<Integer> list = new LinkedList<>();
        int num = k - 1;

        while (num >= 2) {
            list.addFirst(num % 2);
            num = num / 2 - 1;
        }
        list.addFirst(num);

        StringBuilder stringBuilder = new StringBuilder();
        for (int digit : list) {
            stringBuilder.append(digit == 0 ? '4' : '7');
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 8 ms (Beats: 64.29%)
- Memory: 44.97 MB (Beats: 40.00%)

<br>
