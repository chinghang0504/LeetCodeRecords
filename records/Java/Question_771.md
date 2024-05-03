# [LeetCode Records](../../README.md) - Question 771 Jewels and Stones

### Attempt 1: Use a HashSet
```java
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        Set<Character> set = new HashSet<>();
        for (char ch : jewels.toCharArray()) {
            set.add(ch);
        }

        int count = 0;
        for (char ch : stones.toCharArray()) {
            if (set.contains(ch)) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 56.72%)
- Memory: 41.70 MB (Beats: 36.08%)

<br>

### Attempt 2: Use two loops
```java
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        int count = 0;

        for (char ch1 : stones.toCharArray()) {
            for (char ch2 : jewels.toCharArray()) {
                if (ch1 == ch2) {
                    count++;
                    break;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.31 MB (Beats: 89.17%)

<br>
