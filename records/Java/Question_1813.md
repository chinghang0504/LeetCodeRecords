# [LeetCode Records](../../README.md) - Question 1813 Sentence Similarity III

### Attempt 1: Compare from the left and from the right
```java
class Solution {
    public boolean areSentencesSimilar(String sentence1, String sentence2) {
        String s1 = sentence1;
        String s2 = sentence2;
        if (sentence1.length() > sentence2.length()) {
            s1 = sentence2;
            s2 = sentence1;
        }

        String[] splits1 = s1.split("\s");
        String[] splits2 = s2.split("\s");

        int leftIndex = 0;
        while (leftIndex < splits1.length && splits1[leftIndex].equals(splits2[leftIndex])) {
            leftIndex++;
        }

        int rightIndex1 = splits1.length - 1;
        int rightIndex2 = splits2.length - 1;
        while (rightIndex1 >= 0 && splits1[rightIndex1].equals(splits2[rightIndex2])) {
            rightIndex1--;
            rightIndex2--;
        }

        return leftIndex > rightIndex1;
    }
}
```
- Runtime: 1 ms (Beats: 99.05%)
- Memory: 41.74 MB (Beats: 47.35%)

<br>
