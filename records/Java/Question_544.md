# [LeetCode Records](../../README.md) - Question 544 Output Contest Matches

### Attempt 1: Use an ArrayList to store the team matches
```java
class Solution {
    public String findContestMatch(int n) {
        List<String> list = new ArrayList<>();
        for (int i = 0; i < n / 2; i++) {
            list.add("(" + (i + 1) + "," + (n - i) + ")");
        }

        int size = list.size();
        while (size >= 2) {
            List<String> nextList = new ArrayList<>();

            for (int i = 0; i < size / 2; i++) {
                String team1 = list.get(i);
                String team2 = list.get(size - i - 1);
                nextList.add("(" + team1 + "," + team2 + ")");
            }

            list = nextList;
            size = list.size();
        }

        return list.get(0);
    }
}
```
- Runtime: 11 ms (Beats: 15.91%)
- Memory: 42.79 MB (Beats: 93.18%)

<br>

### Attempt 2: Use a String[] to store the team matches
```java
class Solution {
    public String findContestMatch(int n) {
        int size = n / 2;
        String[] arr = new String[size];

        for (int i = 0; i < size; i++) {
            arr[i] = "(" + (i + 1) + "," + (n - i) + ")";
        }

        while (size >= 2) {
            int nextSize = size / 2;
            for (int i = 0; i < nextSize; i++) {
                String team1 = arr[i];
                String team2 = arr[size - i - 1];
                arr[i] = "(" + team1 + "," + team2 + ")";
            }

            size = nextSize;
        }

        return arr[0];
    }
}
```
- Runtime: 11 ms (Beats: 15.91%)
- Memory: 42.63 MB (Beats: 95.45%)

<br>
