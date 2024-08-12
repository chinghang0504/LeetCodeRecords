# [LeetCode Records](../../README.md) - Question 2423 Remove Letter To Equalize Frequency

### Attempt 1: Use an int[] to save the character counts and a HashMap to save the frequencies of character counts
```java
class Solution {
    public boolean equalFrequency(String word) {
        int[] counts = new int[26];
        for (char ch : word.toCharArray()) {
            counts[ch - 'a']++;
        }

        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < 26; i++) {
            if (counts[i] != 0) {
                map.merge(counts[i], 1, Integer::sum);
            }
        }

        int size = map.size();
        if (size > 2) {
            return false;
        }

        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(map.entrySet());
        Map.Entry<Integer, Integer> entry1 = list.get(0);
        int count1 = entry1.getKey();
        int freq1 = entry1.getValue();

        if (size == 1) {
            if (freq1 == 1) {
                return true;
            } else {
                return count1 == 1;
            }
        }

        Map.Entry<Integer, Integer> entry2 = list.get(1);
        int count2 = entry2.getKey();
        int freq2 = entry2.getValue();

        if (freq1 == 1 && (count1 == 1 || count1 - 1 == count2)) {
            return true;
        }
        if (freq2 == 1 && (count2 == 1 || count2 - 1 == count1)) {
            return true;
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 57.05%)
- Memory: 41.16 MB (Beats: 72.25%)

<br>
