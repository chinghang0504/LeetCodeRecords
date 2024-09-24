# [LeetCode Records](../../README.md) - Question 763 Partition Labels

### Attempt 1: Use an int[] to store the last index of characters
```java
class Solution {
    public List<Integer> partitionLabels(String s) {
        int[] lastIndices = new int[26];
        char[] arr = s.toCharArray();
        for (int i = 0; i < arr.length; i++) {
            lastIndices[arr[i] - 'a'] = i;
        }

        List<Integer> ans = new ArrayList<>();
        int prevLastIndex = -1;
        int currMaxLastIndex = 0;
        for (int i = 0; i < arr.length; i++) {
            currMaxLastIndex = Math.max(currMaxLastIndex, lastIndices[arr[i] - 'a']);
            
            if (currMaxLastIndex == i) {
                ans.add(currMaxLastIndex - prevLastIndex);
                prevLastIndex = currMaxLastIndex;
            }
        }

        return ans;
    }
}
```
- Runtime: 2 ms (Beats: 99.86%)
- Memory: 41.53 MB (Beats: 98.30%)

<br>
