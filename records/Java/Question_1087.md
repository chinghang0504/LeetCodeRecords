# [LeetCode Records](../../README.md) - Question 1087 Brace Expansion

### Attempt 1: Use an ArrayList to store the StringBuilder
```java
class Solution {
    public String[] expand(String s) {
        List<StringBuilder> list = new ArrayList<>();
        list.add(new StringBuilder());
        char[] arr = s.toCharArray();

        int i = 0;
        while (i < arr.length) {
            if (arr[i] == '{') {
                List<Character> chList = new ArrayList<>();
                i++;
                while (true) {
                    chList.add(arr[i]);
                    if (arr[i + 1] == ',') {
                        i += 2;
                    } else {
                        break;
                    }
                }
                list = updateList(list, chList);
                i += 2;
            } else {
                for (StringBuilder stringBuilder : list) {
                    stringBuilder.append(arr[i]);
                }
                i++;
            }
        }

        String[] ans = list.stream().map(StringBuilder::toString).toArray(String[]::new);
        Arrays.sort(ans);
        return ans;
    }

    private List<StringBuilder> updateList(List<StringBuilder> prevList, List<Character> chList) {
        List<StringBuilder> list = new ArrayList<>();

        for (char ch : chList) {
            for (StringBuilder stringBuilder : prevList) {
                StringBuilder nextStringBuilder = new StringBuilder(stringBuilder.toString());
                nextStringBuilder.append(ch);
                list.add(nextStringBuilder);
            }
        }

        return list;
    }
}
```
- Runtime: 7 ms (Beats: 28.96%)
- Memory: 44.26 MB (Beats: 97.30%)

<br>
