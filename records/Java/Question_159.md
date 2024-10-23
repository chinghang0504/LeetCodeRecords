# [LeetCode Records](../../README.md) - Question 159 Longest Substring with At Most Two Distinct Characters

### Attempt 1: Use two int[] to store the character counts
```java
class Solution {
    public int lengthOfLongestSubstringTwoDistinct(String s) {
        char[] arr = s.toCharArray();
        int[] upperCaseCounts = new int[26];
        int[] lowerCaseCounts = new int[26];

        int maxCount = 0;
        int startIndex = 0;
        for (int i = 0; i < arr.length; i++) {
            if (Character.isUpperCase(arr[i])) {
                upperCaseCounts[arr[i] - 'A']++;
            } else {
                lowerCaseCounts[arr[i] - 'a']++;
            }

            if (isValid(upperCaseCounts, lowerCaseCounts)) {
                maxCount = Math.max(maxCount, i - startIndex + 1);
            } else {
                if (Character.isUpperCase(arr[startIndex])) {
                    upperCaseCounts[arr[startIndex] - 'A']--;
                } else {
                    lowerCaseCounts[arr[startIndex] - 'a']--;
                }
                startIndex++;
            }
        }

        return maxCount;
    }

    private boolean isValid(int[] upperCaseCounts, int[] lowerCaseCounts) {
        int count = 0;

        for (int upperCaseCount : upperCaseCounts) {
            if (upperCaseCount > 0) {
                count++;

                if (count > 2) {
                    return false;
                }
            }
        }
        for (int lowerCaseCount : lowerCaseCounts) {
            if (lowerCaseCount > 0) {
                count++;

                if (count > 2) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 42 ms (Beats: 49.87%)
- Memory: 45.38 MB (Beats: 38.89%)

<br>

### Attempt 2: Use a HashMap to store the character counts
```java
class Solution {
    public int lengthOfLongestSubstringTwoDistinct(String s) {
        char[] arr = s.toCharArray();
        Map<Character, Integer> map = new HashMap<>();

        int maxCount = 0;
        int startIndex = 0;
        for (int i = 0; i < arr.length; i++) {
            map.merge(arr[i], 1, Integer::sum);

            if (map.size() <= 2) {
                maxCount = Math.max(maxCount, i - startIndex + 1);
            } else {
                Integer count = map.get(arr[startIndex]);
                if (count == 1) {
                    map.remove(arr[startIndex]);
                } else {
                    map.put(arr[startIndex], count - 1);
                }
                startIndex++;
            }
        }

        return maxCount;
    }
}
```
- Runtime: 40 ms (Beats: 57.33%)
- Memory: 45.36 MB (Beats: 38.89%)

<br>
