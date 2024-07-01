# [LeetCode Records](../../README.md) - Question 2678 Number of Senior Citizens

### Attempt 1: Use Integer.valueOf() and substring()
```java
class Solution {
    public int countSeniors(String[] details) {
        int count = 0;

        for (String detail : details) {
            int age = Integer.valueOf(detail.substring(11, 13));
            if (age > 60) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 81.14%)
- Memory: 42.28 MB (Beats: 73.09%)

<br>

### Attempt 2: Use charAt()
```java
class Solution {
    public int countSeniors(String[] details) {
        int count = 0;

        for (String detail : details) {
            char firstCh = detail.charAt(11);
            if (firstCh > '6' || (firstCh == '6' && detail.charAt(12) > '0')) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.98 MB (Beats: 92.99%)

<br>
