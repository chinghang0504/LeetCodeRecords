# [LeetCode Records](../../README.md) - Question 3006 Find Beautiful Indices in the Given Array I

### Attempt 1: Use two ArrayList to store the indices of String a and String b
```java
class Solution {
    public List<Integer> beautifulIndices(String s, String a, String b, int k) {
        char[] arr = s.toCharArray();
        char[] aArr = a.toCharArray();
        char[] bArr = b.toCharArray();
        List<Integer> aList = new ArrayList<>();
        List<Integer> bList = new ArrayList<>();

        for (int i = 0; i < arr.length - aArr.length + 1; i++) {
            if (isEqual(arr, aArr, i)) {
                aList.add(i);
            }
        }
        for (int i = 0; i < arr.length - bArr.length + 1; i++) {
            if (isEqual(arr, bArr, i)) {
                bList.add(i);
            }
        }

        int aListSize = aList.size();
        int bListSize = bList.size();
        List<Integer> ans = new ArrayList<>();
        for (int i = 0, j = 0; i < aListSize && j < bListSize;) {
            int aIndex = aList.get(i);
            int bIndex = bList.get(j);
            if (Math.abs(bIndex - aIndex) <= k) {
                ans.add(aIndex);
                i++;
            } else if (bIndex < aIndex) {
                j++;
            } else {
                i++;
            }
        }

        return ans;
    }

    private boolean isEqual(char[] arr, char[] wordArr, int start) {
        for (int i = 0; i < wordArr.length; i++) {
            if (arr[start + i] != wordArr[i]) {
                return false;
            }
        }
        return true;
    }
}
```
- Runtime: 9 ms (Beats: 82.05%)
- Memory: 47.51 MB (Beats: 41.99%)

<br>
