# [LeetCode Records](../../README.md) - Question 386 Lexicographical Numbers

### Attempt 1: Use recursion
```java
class Solution {
    public List<Integer> lexicalOrder(int n) {
        List<Integer> ans = new ArrayList<>();

        for (int i = 1; i <= 9; i++) {
            lexicalOrderRecursion(n, ans, i);
        }

        return ans;
    }

    private void lexicalOrderRecursion(int n, List<Integer> ans, int num) {
        if (num > n) {
            return;
        }

        ans.add(num);

        num *= 10;
        for (int i = 0; i <= 9; i++) {
            int nextNum = num + i;
            if (nextNum > n) {
                break;
            }
            
            lexicalOrderRecursion(n, ans, nextNum);
        }
    }
}
```
- Runtime: 1 ms (Beats: 99.99%)
- Memory: 48.01 MB (Beats: 83.83%)

<br>
