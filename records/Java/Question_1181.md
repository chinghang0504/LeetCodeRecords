# [LeetCode Records](../../README.md) - Question 1181 Before and After Puzzle

### Attempt 1: Test every case
```java
class Solution {

    class Item {
        String phrase;
        String firstWord;
        String lastWord;

        Item(String phrase) {
            String[] splits = phrase.split("\s");
            this.phrase = phrase;
            this.firstWord = splits[0];
            this.lastWord = splits[splits.length - 1];
        }
    }

    public List<String> beforeAndAfterPuzzles(String[] phrases) {
        Item[] items = new Item[phrases.length];
        for (int i = 0; i < phrases.length; i++) {
            items[i] = new Item(phrases[i]);
        }

        Set<String> set = new HashSet<>();
        for (int i = 0; i < phrases.length; i++) {
            for (int j = 0; j < phrases.length; j++) {
                if (i != j && items[i].lastWord.equals(items[j].firstWord)) {
                    int commonSize = items[j].firstWord.length();
                    String firstStr = items[i].phrase;
                    String secondStr = items[j].phrase.substring(commonSize);
                    set.add(firstStr + secondStr);
                }
            }
        }

        List<String> ans = new ArrayList<>(set);
        ans.sort((s1, s2) -> s1.compareTo(s2));

        return ans;
    }
}
```
- Runtime: 9 ms (Beats: 66.67%)
- Memory: 44.77 MB (Beats: 80.00%)

<br>
