# [LeetCode Records](../../README.md) - Question 299 Bulls and Cows

### Attempt 1: Use String.format()
```java
class Solution {
    public String getHint(String secret, String guess) {
        char[] arr1 = secret.toCharArray();
        char[] arr2 = guess.toCharArray();
        int[] counts1 = new int[10];
        int[] counts2 = new int[10];
        int numOfBulls = 0;
        
        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] == arr2[i]) {
                numOfBulls++;
            } else {
                counts1[arr1[i] - '0']++;
                counts2[arr2[i] - '0']++;
            }
        }

        int numOfCows = 0;
        for (int i = 0; i < 10; i++) {
            numOfCows += Math.min(counts1[i], counts2[i]);
        }

        return String.format("%dA%dB", numOfBulls, numOfCows);
    }
}
```
- Runtime: 4 ms (Beats: 90.98%)
- Memory: 42.48 MB (Beats: 31.25%)

<br>

### Attempt 2: Use StringBuilder
```java
class Solution {
    public String getHint(String secret, String guess) {
        char[] arr1 = secret.toCharArray();
        char[] arr2 = guess.toCharArray();
        int[] counts1 = new int[10];
        int[] counts2 = new int[10];
        int numOfBulls = 0;
        
        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] == arr2[i]) {
                numOfBulls++;
            } else {
                counts1[arr1[i] - '0']++;
                counts2[arr2[i] - '0']++;
            }
        }

        int numOfCows = 0;
        for (int i = 0; i < 10; i++) {
            numOfCows += Math.min(counts1[i], counts2[i]);
        }

        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append(numOfBulls);
        stringBuilder.append('A');
        stringBuilder.append(numOfCows);
        stringBuilder.append('B');
        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.47 MB (Beats: 31.25%)

<br>
