# [LeetCode Records](../../README.md) - Question 792 Number of Matching Subsequences

### Attempt 1: Check every word
```java
class Solution {
    public int numMatchingSubseq(String s, String[] words) {
        char[] arr = s.toCharArray();

        int count = 0;
        for (String word : words) {
            if (isMatched(arr, word.toCharArray())) {
                count++;
            }
        }

        return count;
    }

    private boolean isMatched(char[] arr1, char[] arr2) {
        if (arr2.length > arr1.length) {
            return false;
        }

        int index1 = 0;
        int index2 = 0;
        while (index1 < arr1.length && index2 < arr2.length) {
            if (arr1[index1] == arr2[index2]) {
                index1++;
                index2++;
            } else {
                index1++;
            }
        }

        return index2 == arr2.length;
    }
}
```
- Runtime: 2355 ms (Beats: 5.02%)
- Memory: 45.87 MB (Beats: 58.09%)

<br>

### Attempt 2: Use a HashMap to store the string counts
```java
class Solution {
    public int numMatchingSubseq(String s, String[] words) {
        Map<String, Integer> map = new HashMap<>();
        for (String word : words) {
            map.merge(word, 1, Integer::sum);
        }

        char[] arr = s.toCharArray();
        int count = 0;
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            if (isMatched(arr, entry.getKey().toCharArray())) {
                count += entry.getValue();
            }
        }

        return count;
    }

    private boolean isMatched(char[] arr1, char[] arr2) {
        if (arr2.length > arr1.length) {
            return false;
        }

        int index1 = 0;
        int index2 = 0;
        while (index1 < arr1.length && index2 < arr2.length) {
            if (arr1[index1] == arr2[index2]) {
                index1++;
                index2++;
            } else {
                index1++;
            }
        }

        return index2 == arr2.length;
    }
}
```
- Runtime: 38 ms (Beats: 80.05%)
- Memory: 45.50 MB (Beats: 83.81%)

<br>
