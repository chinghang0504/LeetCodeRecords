# [LeetCode Records](../../README.md) - Question 3304 Find the K-th Character in String Game I

### Attempt 1: Use a while loop to exeucte the operation
```java
class Solution {
    public char kthCharacter(int k) {
        String word = "a";

        while (word.length() < k) {
            StringBuilder stringBuilder = new StringBuilder();
            stringBuilder.append(word);

            for (char ch : word.toCharArray()) {
                char nextCh = ch != 'z' ? (char)(ch + 1) : 'a';
                stringBuilder.append(nextCh);
            }
            
            word = stringBuilder.toString();
        }

        return word.charAt(k - 1);
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 42.86 MB (Beats: 100.00%)

<br>
