# [LeetCode Records](../../README.md) - Question 1119 Remove Vowels from a String

### Attempt 1: Use replaceAll()
```java
class Solution {
    public String removeVowels(String s) {
        return s.replaceAll("[aeiou]+", "");
    }
}
```
- Runtime: 1 ms (Beats: 65.59%)
- Memory: 41.30 MB (Beats: 51.77%)

<br>

### Attempt 2: Use an if statement (AND)
```java
class Solution {
    public String removeVowels(String s) {
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : s.toCharArray()) {
            if (ch != 'a' && ch != 'e' && ch != 'i' && ch != 'o' && ch != 'u') {
                stringBuilder.append(ch);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.81 MB (Beats: 97.43%)

<br>

### Attempt 3: Use an if statement (OR)
```java
class Solution {
    public String removeVowels(String s) {
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : s.toCharArray()) {
            if (!(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u')) {
                stringBuilder.append(ch);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.32 MB (Beats: 51.77%)

<br>
