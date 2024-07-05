# [LeetCode Records](../../README.md) - Question 1880 Check if Word Equals Summation of Two Words

### Attempt 1: Use a helper function to calculate the numerical value
```java
class Solution {
    public boolean isSumEqual(String firstWord, String secondWord, String targetWord) {
        int value1 = getNumericalValue(firstWord);
        int value2 = getNumericalValue(secondWord);
        int valueTarget = getNumericalValue(targetWord);

        return value1 + value2 == valueTarget;
    }

    private int getNumericalValue(String word) {
        char[] arr = word.toCharArray();
        int sum = 0;
        int multiplier = 1;

        for (int i = arr.length - 1; i >= 0; i--) {
            sum += (arr[i] - 'a') * multiplier;
            multiplier *= 10;
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.57 MB (Beats: 29.41%)

<br>
