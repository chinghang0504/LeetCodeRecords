# [LeetCode Records](../README.md) - Question 202 Happy Number

### Attempt 1: 
```java
class Solution {
    HashSet<Integer> hashSet = new HashSet<>();

    public boolean isHappy(int n) {
        return isHappyRecursion(n);
    }

    boolean isHappyRecursion(int n) {
        if (hashSet.contains(n)) {
            return false;
        } else {
            hashSet.add(n);
        }

        int count = 0;
        while (n > 9) {
            int val = n % 10;
            count += val * val;
            n /= 10;
        }
        int val = n % 10;
        count += val * val;

        if (count == 1) {
            return true;
        }

        return isHappyRecursion(count);
    }
}
```
- Runtime: 1 ms (Beats: 64.01%)
- Memory: 40.68 MB (Beats: 48.75%)

<br>
