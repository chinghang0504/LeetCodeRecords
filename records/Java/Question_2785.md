# [LeetCode Records](../../README.md) - Question 2785 Sort Vowels in a String

### Attempt 1: Use an ArrayList to save the indices of vowels
```java
class Solution {
    public String sortVowels(String s) {
        char[] arr = s.toCharArray();
        List<Integer> vowelIndexList = new ArrayList<>();

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == 'A' || arr[i] == 'E' || arr[i] == 'I' || arr[i] == 'O' || arr[i] == 'U' ||
                arr[i] == 'a' || arr[i] == 'e' || arr[i] == 'i' || arr[i] == 'o' || arr[i] == 'u'
            ) {
                vowelIndexList.add(i);
            }
        }

        char[] vowelArr = new char[vowelIndexList.size()];
        int i = 0;
        for (int vowelIndex : vowelIndexList) {
            vowelArr[i] = arr[vowelIndex];
            i++;
        }

        Arrays.sort(vowelArr);
        
        i = 0;
        for (int vowelIndex : vowelIndexList) {
            arr[vowelIndex] = vowelArr[i];
            i++;
        }

        return new String(arr);
    }
}
```
- Runtime: 15 ms (Beats: 94.91%)
- Memory: 47.99 MB (Beats: 42.23%)

<br>
