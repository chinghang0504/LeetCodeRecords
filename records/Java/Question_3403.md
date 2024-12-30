# [LeetCode Records](../../README.md) - Question 3403 Find the Lexicographically Largest String From the Box I

### Attempt 1: Use an ArrayList to store the indices of the current maximum characters
```java
class Solution {
    public String answerString(String word, int numFriends) {
        if (numFriends == 1)  {
            return word;
        }
        
        char[] arr = word.toCharArray();
        int maxLen = arr.length - numFriends + 1;

        char firstMaxCh = arr[0];
        List<Integer> prevList = new ArrayList<>();
        prevList.add(0);
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > firstMaxCh) {
                prevList.clear();
                prevList.add(i);
                firstMaxCh = arr[i];
            } else if (arr[i] == firstMaxCh) {
                prevList.add(i);
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append(firstMaxCh);

        for (int i = 1; i < maxLen && !prevList.isEmpty(); i++) {
            List<Integer> list = new ArrayList<>();
            int size = prevList.size();

            int index = prevList.get(0) + 1;
            if (index >= arr.length) {
                break;
            }
            char currMaxCh = arr[index];
            list.add(index);

            for (int j = 1; j < size; j++) {
                int nextIndex = prevList.get(j) + 1;
                if (nextIndex >= arr.length) {
                    break;
                }

                if (arr[nextIndex] > currMaxCh) {
                    list.clear();
                    list.add(nextIndex);
                    currMaxCh = arr[nextIndex];
                } else if (arr[nextIndex] == currMaxCh) {
                    list.add(nextIndex);
                }
            }

            stringBuilder.append(currMaxCh);
            prevList = list;
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 128 ms (Beats: 100.00%)
- Memory: 45.44 MB (Beats: 100.00%)

<br>
