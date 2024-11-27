# [LeetCode Records](../../README.md) - Question 2840 Check if Strings Can be Made Equal With Operations II

### Attempt 1: Record the odd and even indices character counts
```java
class Solution {
    public boolean checkStrings(String s1, String s2) {
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        int[] evenCounts1 = new int[26];
        int[] oddCounts1 = new int[26];
        int[] evenCounts2 = new int[26];
        int[] oddCounts2 = new int[26];

        for (int i = 0; i < arr1.length; i++) {
            if (i % 2 == 0) {
                evenCounts1[arr1[i] - 'a']++;
                evenCounts2[arr2[i] - 'a']++;
            } else {
                oddCounts1[arr1[i] - 'a']++;
                oddCounts2[arr2[i] - 'a']++;
            }
        }

        for (int i = 0; i < 26; i++) {
            if (evenCounts1[i] != evenCounts2[i] || oddCounts1[i] != oddCounts2[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 5 ms (Beats: 90.63%)
- Memory: 45.05 MB (Beats: 100.00%)

<br>
